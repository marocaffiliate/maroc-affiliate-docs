# Purchase Return (Stock Out)

## What This Page Does
When admin returns purchased products, the system removes returned quantities from **Main Stock**.

---

## Input Methods

| Method | Use Case |
|--------|----------|
| **QR Scanner** | Scan item barcode and add it to return cart |
| **Manual Selection** | Select purchased variant and set return quantity |

Both methods add items to the same return cart.

---

## What Happens On Confirm Return

When admin clicks **Process Return**, the system does this:

1. Creates a **Return Batch**
2. Allocates returned quantities against confirmed purchases (FIFO)
3. Creates **Return rows** linked to original purchase rows
4. Updates **Main Stock** by **decrementing quantity**
5. Creates a **Stock Movement** with type `RETURN`

---

## Stock Movement Effect

| Field | Value |
|------|-------|
| **Type** | `RETURN` |
| **From Location** | `MAIN_STOCK` |
| **To Location** | `MAIN_STOCK` |
| **Quantity Stored** | Negative (`-quantity`) |
| **Main Stock Effect** | Decrease quantity |

---

## Validation Before Processing

The page blocks return if:

- Requested quantity is more than available in Main Stock
- There are not enough confirmed purchases to cover returned quantity

Each line can include an optional return reason.

---

## Permission

- `returns:create`
