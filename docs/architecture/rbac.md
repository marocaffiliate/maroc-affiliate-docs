# RBAC (Roles & Permissions)

## Overview

RBAC in marocAffiliate is **permission-first**.

- Pages/actions check permissions (not hardcoded role names)
- Roles are collections of permissions
- Users can have multiple roles
- Effective access is computed at runtime

---

## Core Data Schema

```prisma
model Role {
  id          String   @id @default(cuid())
  name        String   @unique
  description String?
  isSystem    Boolean  @default(false)

  users       UserRole[]
  permissions RolePermission[]
}

model Permission {
  id          String   @id @default(cuid())
  name        String   @unique
  description String?
  module      String

  roles RolePermission[]
}

model RolePermission {
  roleId       String
  permissionId String

  role       Role       @relation(fields: [roleId], references: [id], onDelete: Cascade)
  permission Permission @relation(fields: [permissionId], references: [id], onDelete: Cascade)

  @@id([roleId, permissionId])
}

model UserRole {
  userId String
  roleId String

  user User @relation(fields: [userId], references: [id], onDelete: Cascade)
  role Role @relation(fields: [roleId], references: [id], onDelete: Cascade)

  @@id([userId, roleId])
}
```

---

## Authorization Flow

### 1) Server-side gate

All protected actions/pages call:

- `requireAuth()`
- `requirePermission("permission:name")`
- `requireAnyPermission([...])`

From: `src/lib/authorize.ts`

### 2) Permission resolution

`hasPermission(userId, permission)` checks user effective permissions from `src/lib/rbac.ts`.

---

## Permission Resolution Logic

## Standard user (non-team-member)

Effective permissions = union of all permissions from all assigned roles.

## Team member user

Effective permissions are not taken directly from global roles.

They are computed as:

`team role permissions` ∩ `parent seller current permissions`

This guarantees team member permissions never exceed the seller's current access.

Also, team members get seller dashboard access when seller has it.

---

## Team Models (Seller Team RBAC)

```prisma
enum TeamMemberStatus {
  PENDING
  ACTIVE
  SUSPENDED
  REMOVED
}

model SellerTeamRole {
  id            String   @id @default(cuid())
  sellerId      String
  name          String
  description   String?
  permissionIds String[]
  isActive      Boolean  @default(true)

  seller      User
  teamMembers SellerTeamMember[]

  @@unique([sellerId, name])
}

model SellerTeamMember {
  id         String @id @default(cuid())
  sellerId   String
  userId     String @unique
  teamRoleId String
  status     TeamMemberStatus @default(ACTIVE)

  seller   User
  user     User
  teamRole SellerTeamRole
}
```

---

## Session & Cache Invalidation

RBAC uses `sessionVersion` in `User` plus in-memory cache.

- Permission cache key: `userId:sessionVersion`
- Permission cache TTL: 60s
- Team-context cache TTL: 5min

When roles/permissions change:

- bump user `sessionVersion`
- record `UserRoleUpdate`
- invalidate in-memory caches

Helpers in `src/lib/rbac.ts`:

- `bumpUserSessionVersion`
- `bumpUsersSessionVersion`
- `invalidateUserPermissionCache`
- `invalidateSellerTeamMemberSessions`
- `invalidateTeamRoleMemberSessions`

---

## Delegation Rules (Seller → Team)

Seller team roles can only use seller-delegatable permissions.

Non-delegatable examples (filtered out):

- `dashboard:admin:access`
- `dashboard:seller:access`
- `dashboard:warehouse:access`
- `dashboard:provider:access`
- `team:manage`

This is enforced by seller delegation helpers in `src/lib/rbac.ts`.

---

## Admin RBAC Management Helpers

`src/lib/rbac-admin.ts` includes helper functions for role/permission management:

- create role
- upsert permission
- assign permissions to role
- assign/revoke role from user

Role assign/revoke automatically bumps user session version.

---

## Practical Rules For Developers

- Always protect server actions with `requirePermission(...)`
- Do not rely on role name checks for access
- Use permission names as the source of truth
- After changing roles/permissions, ensure session version bump/invalidation path runs
- For seller team features, always treat seller permissions as the ceiling
