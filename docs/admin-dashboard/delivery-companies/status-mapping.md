# Status Mapping

## What This Page Does

Admin maps each external company status to one internal delivery status used by marocAffiliate.

Model: `DeliveryStatusMapping`

- one external status -> one internal status
- many external statuses can map to the same internal status

---

## Why Mapping Matters

Webhook updates and manual sync flows rely on this mapping to drive business outcomes.

Without mapping:

- webhook update is logged but cannot update lifecycle correctly (`MAPPING_NOT_FOUND`)
- delivery/order state transitions are blocked for that status

---

## Business Impact of Internal Status

Mapped internal status affects parent order behavior:

- success terminal statuses (for example `DELIVERED`) -> order goes to `COMPLETED`
- return/failure terminal statuses (for example `RETURNED`, `REFUSED`, `CANCELLED`, `DAMAGED`) -> order goes to `RETURNED` and stock restore flow runs

Benefits/liability logic also depends on these transitions.

---

## Mapping Workflow

1. import/create external statuses
2. map each status to internal status
3. save changes in bulk
4. keep terminal statuses aligned with real carrier behavior

Tip: prioritize mapping all statuses used by webhook first to avoid pending/error webhook logs.
