# Statuses

## What This Page Does

Admin manages external statuses for each delivery company.

A status includes:

- `code` (provider status code)
- `name`
- optional description and color
- classification flags (`isTerminal`, `isSuccess`, `isFailure`)

---

## How Admin Adds Statuses

Two options:

- **Manual**: create one status at a time
- **CSV import**: bulk import with header format:

```text
code,name,description,color,isTerminal,isSuccess,isFailure,internalStatus
```

If `internalStatus` is provided and valid, mapping is created during import.

---

## Delete Behavior

Delete is safe by design:

- if status is already used in delivery orders/history -> soft-delete (`isActive=false`)
- if not used -> hard delete

This prevents breaking historical delivery records.

---

## Company-Specific Note (GLOG)

Webhook processing includes fallback logic for GLOG:

- if webhook sends unknown GLOG status
- system can auto-create that external status and auto-map it (when resolvable)

Admin should still review mappings and naming for consistency.
