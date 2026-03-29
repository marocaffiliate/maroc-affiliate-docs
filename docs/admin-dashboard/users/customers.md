# Customers Page

## What This Page Does

Admin uses this page to manage customer accounts, loyalty cards, and customer status.

---

## What Admin Can Do

### Browse and filter customers

- Search by customer name or phone
- Filter by:
  - status (`active` / `blacklisted`)
  - loyalty card (has card / no card)
  - date range

### View customer stats

Per customer, the page aggregates:

- total orders
- total POS sales
- total amount spent
- loyalty points balance

### Manage customer account

- update basic customer info (name/phone)
- blacklist / unblacklist customer

### Manage loyalty card

- create loyalty card
- activate/deactivate loyalty card
- add or deduct loyalty points (manual adjustment)

### Delete customer (with guard)

Deletion is blocked if customer has order or POS transaction history.

---

## Data Scope

The customers module supports context-based scope:

| Context | Scope |
|--------|-------|
| `admin` | All customers |
| `warehouse` | Customers linked to that warehouse orders/POS |

(Admin page uses `admin` context.)

---

## Permissions

- View: `customers:view`
- Manage: `customers:manage`
