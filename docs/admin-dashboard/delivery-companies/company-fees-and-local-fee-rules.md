# Company Fees & Local Fee Rules

## What This Page Does

Inside a delivery company, admin manages city fee rows used when creating and pricing orders.

Each city row is a `DeliveryFee` record with:

- `city`
- `fee` (inter-city fee)
- `localFee` (optional)
- `returnFee`
- `deliveryType` (`LOCAL` or `INTER_CITY`)
- warehouse links

---

## Local Fee vs Inter-City Fee (Important)

The system does **not** apply local fee only by city name match.

Local fee is applied only when all conditions are true:

1. destination city matches a city row
2. there is a `DeliveryFeeWarehouse` link for this warehouse and city
3. that link has `isLocalFeeLink = true`
4. the fee row is of type `LOCAL`

If these conditions are not met, the system falls back to regular `fee` (inter-city behavior).

---

## Why Warehouse Links Matter

`DeliveryFeeWarehouse` links support two separate behaviors:

- `isLocalFeeLink=true`: enables local fee calculation path
- `isVisible`: controls city visibility in warehouse city selector

These are independent controls. A city can be visible but not local-fee-linked.

---

## City Source and Sync

- For some companies (currently GLOG), admin can use **Sync Cities**.
- Sync creates new `DeliveryFee` rows with default values:
  - `fee = 40`
  - `returnFee = 10`
  - `deliveryType = INTER_CITY`
- Existing city/reference rows are skipped.

---

## Order Handover Dependency

When sending order to delivery, destination city must have an external reference:

- from `externalCityId` or `reference` (company-specific resolver)
- if missing, order is rejected from handover with validation error

---

## Practical Tips

- Configure local fees only where same-city warehouse delivery is truly supported.
- Keep `returnFee` accurate because return statuses can impact seller liabilities/benefits flows.
- After city sync, review pricing before operational use (defaults are placeholders).
