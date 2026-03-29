# Stock Integrity

## What This Page Does

This page verifies whether warehouse stock matches expected stock based on transfers, sales, and returns.

---

## How Expected Stock Is Calculated

Per variant in a selected warehouse:

`Expected Quantity = Transferred In - Sold (orders) - POS Sold + Returned`

`Expected Reserved = NOT_CONFIRMED order quantity`

The page compares expected values vs current warehouse stock values.

---

## What A Discrepancy Means

A discrepancy appears when either of these differs:

- Current quantity vs expected quantity
- Current reserved vs expected reserved

The table shows product, variant, current, expected, and difference.

---

## Fix Actions

### Fix Single Discrepancy

The system attempts to restore stock from missing return effects first.

If no specific return link is found, it applies manual correction:

- Updates warehouse stock quantity
- Creates stock movement type `ADJUSTMENT`

### Fix All

Runs the same correction logic for all listed discrepancies in the selected warehouse.

---

## Stock Movement Types Used

| Action | Movement Type |
|--------|---------------|
| Restore from missed return | `RETURN` |
| Manual correction | `ADJUSTMENT` |

---

## Permissions

- Verify/report view: `stock:view`
- Fix discrepancies: `stock:manage`
