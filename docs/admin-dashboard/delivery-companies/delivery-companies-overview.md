# Delivery Companies Overview

## What This Area Does

Admin uses this area to configure external delivery providers used by warehouses and order handover.

Main responsibilities:

- create/update delivery companies
- assign a company to warehouses
- maintain city fee tables per company
- configure API credentials
- manage external statuses and status mappings
- monitor and retry webhook updates

---

## Pages in This Section

- **Delivery Companies List**: create/edit/delete companies
- **Company Fees & Local Fee Rules**: city pricing and warehouse links
- **API Settings**: save and test provider credentials
- **Statuses**: import/create external statuses
- **Status Mapping**: map external statuses to internal delivery statuses
- **Webhook Logs**: inspect incoming webhooks and retry failed processing

---

## Permissions

- View delivery companies: `delivery-companies:view`
- Manage companies/settings/statuses: `delivery-companies:manage`
- Send orders/update delivery lifecycle: `delivery:manage`

---

## Core Business Rules

### Company lifecycle

- company `name` and `code` must be unique
- delete is blocked if company is still linked to warehouses
- delete is blocked if company still has city/fee rows

### Warehouse relation

- one warehouse links to one delivery company
- orders from that warehouse use that company integration for parcel creation

### Delivery setup dependency

Before sending orders to delivery, company setup must include:

- assigned company on warehouse
- valid city external reference for destination city
- imported statuses
- at least one external -> internal status mapping
- valid API credentials (for external APIs)
