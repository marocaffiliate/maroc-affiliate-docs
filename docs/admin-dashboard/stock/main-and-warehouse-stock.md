# Main & Warehouse Stock

## What These Pages Do

These pages let admin monitor stock in two locations:

| Page | Purpose |
|------|---------|
| **Main Stock** | Central stock before distribution |
| **Warehouse Stock** | Stock already distributed to each warehouse |

---

## Main Stock Page

Main stock is the source used for distribution.

### How stock gets into Main Stock

- **Purchases** add quantity to Main Stock
- Purchase flow creates stock movement type `PURCHASE`

### What admin can do on Main Stock page

- View stock statistics (total, available, reserved)
- Search/filter products and variants
- Open product stock details and movement history
- Start transfer to warehouse
- Open **Add Stock** (purchase) flow

---

## Warehouse Stock Page

Warehouse stock shows what each warehouse currently has.

### How stock appears in warehouses

- Stock arrives via transfer from Main Stock
- Warehouse stock is tracked per product variant assignment

### What admin can do on Warehouse Stock page

- Select warehouse and view overview stats
- View available vs reserved quantity
- Filter by search, category, stock level
- See stock movement history for selected warehouse

---

## Stock Meaning

| Metric | Meaning |
|--------|---------|
| **Quantity** | Total units at that location |
| **Reserved** | Units allocated to pending orders |
| **Available** | `Quantity - Reserved` |

---

## Permissions

- `stock:view`
