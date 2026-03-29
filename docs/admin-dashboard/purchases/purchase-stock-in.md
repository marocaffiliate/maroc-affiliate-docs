# Purchase (Stock In)

## What This Page Does
When admin confirms a purchase, the system adds products into **Main Stock**.

---

## Input Methods

| Method | Use Case |
|--------|----------|
| **QR Scanner** | Fast intake by scanning product QR codes |
| **Manual Selection** | Add product variants and quantities without scanning |

Both methods add items to the same purchase cart.

---

## What Happens On Confirm Purchase

When admin clicks **Process Purchase**, the system does this for each cart item:

1. Creates a **Purchase Batch** (the header record)
2. Creates **Purchase rows** per item (status: confirmed)
3. Creates a **Stock Movement** with type `PURCHASE`
4. Updates **Main Stock** by **incrementing quantity**
5. Sets related barcode location to **MAIN_STOCK**
6. Adds barcode scan audit entry (when barcode exists)

---

## Stock Movement Effect

| Field | Value |
|------|-------|
| **Type** | `PURCHASE` |
| **From Location** | Not used for purchase-in |
| **To Location** | `MAIN_STOCK` |
| **Quantity Effect** | `+quantity` in Main Stock |

---

## Validation Before Processing

The page validates cart items before final processing:

- Variant assignment still exists and is active
- Shows warning if buy price changed
- Shows warning if item already has stock

If validation fails, purchase is blocked.

---

## Permission

- `purchases:create`
