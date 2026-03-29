# API Settings

## What This Page Does

Admin stores and tests delivery provider credentials used for parcel creation and provider calls.

The form is provider-specific:

- **Ozone**: `customerId` + `apiKey`
- **GLOG**: `specialToken`

---

## Behavior

- credentials are stored in company API fields (`apiKeyEncrypted` path is used)
- UI shows masked credentials after save
- admin can run **Test Connection** before/after saving
- updating credentials takes effect immediately for new delivery operations

---

## Why This Is Critical

Without valid credentials:

- `sendOrdersToDelivery` fails for that company
- parcel creation cannot proceed
- no tracking numbers are created in app

---

## Related Setup Checklist

API settings alone are not enough. Also ensure:

1. warehouse is linked to this company
2. company statuses are imported/created
3. statuses are mapped to internal statuses
4. destination cities have external references
