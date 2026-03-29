# Stock Transfer (Main → Warehouse)

## What This Page Does

The transfer page moves stock from **Main Stock** to a selected **Warehouse**.

---

## Transfer Flow

Admin can build transfer cart by:

| Method | How |
|--------|-----|
| **Scan Mode** | Scan barcode to add variant to cart |
| **Browse Mode** | Add product variants manually |
| **Cart Tab** | Review and edit transfer lines |

At checkout, admin selects destination warehouse and confirms transfer.

---

## Validation Before Transfer

Transfer is blocked if:

- Warehouse is not active
- Variant assignment is invalid
- Requested quantity is zero
- Requested quantity is more than available in Main Stock

Barcode scan also validates assignment + barcode existence.

---

## What Happens On Confirm Transfer

For each transfer line, the system:

1. Decrements **Main Stock** quantity
2. Increments (or creates) **Warehouse Stock** quantity
3. Creates stock movement type `TRANSFER`

---

## Stock Movement Effect

| Field | Value |
|------|-------|
| **Type** | `TRANSFER` |
| **From Location** | `MAIN_STOCK` |
| **To Location** | `WAREHOUSE` |
| **To Warehouse** | Selected warehouse |
| **Quantity Effect** | Main stock `-qty`, warehouse stock `+qty` |

---

## Permissions

- `stock:transfer`
