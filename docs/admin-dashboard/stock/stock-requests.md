# Stock Requests

## What This Page Does

Admin uses this page to manage stock requests made between warehouses or from main stock.

---

## Request Sources

| Source Type | Meaning |
|------------|---------|
| `MAIN_STOCK` | Requesting warehouse asks stock from main stock |
| `WAREHOUSE` | Requesting warehouse asks stock from another warehouse |

---

## Request Workflow (Admin)

Requests move through statuses like:

- `PENDING`
- `REVIEWING`
- `APPROVED` / `PARTIALLY_APPROVED` / `REJECTED`
- `FULFILLING`
- `COMPLETED`

Admin can review quantities, add notes, and fulfill approved requests.

---

## What Happens On Fulfill

When admin fulfills a request, stock is transferred and request becomes `COMPLETED`.

### If source is Main Stock

For each approved item:

1. Main stock quantity decreases
2. Requesting warehouse stock increases
3. Stock movement is created with type `TRANSFER`
   - from `MAIN_STOCK`
   - to `WAREHOUSE`

### If source is another Warehouse

For each approved item:

1. Source warehouse stock decreases
2. Requesting warehouse stock increases
3. Stock movement is created with type `TRANSFER`
   - from `WAREHOUSE` (source warehouse)
   - to `WAREHOUSE` (requesting warehouse)

---

## Notes

- Direct status change to `COMPLETED` is blocked in admin action
- Completion must go through fulfill flow so stock movement is recorded correctly

---

## Permissions

- View: `stock-requests:view`
- Approve/Fulfill: `stock-requests:approve`
