# Users Page

## What This Page Does

Admin uses this page to manage platform user accounts and role assignment.

---

## What Admin Can Do

### Browse and filter users

- search by first name, last name, or phone
- filter by:
  - email
  - admin verification status
  - role
  - seller type
  - created date range

### View account overview

The page includes counts for:

- verified vs unverified users
- users per role

### Manage user accounts

- create user
- update user profile fields
- update verification status
- delete users

### Manage user role access

- assign role on user update
- update user role set
- role changes trigger session version increment (session invalidation)

---

## Key Business Rules

- Store name must be unique (when updating seller store name)
- If admin verifies user and email is not verified yet, `emailVerified` is set
- Role changes invalidate existing sessions by bumping `sessionVersion`

---

## Permissions

- View users: `users:view`
- Manage users: `users:manage`
- Assign roles: `users:assign-role`
