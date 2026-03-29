# Warehouses Page

## What This Page Does

Admin uses this page to manage warehouses, warehouse managers, delivery company linkage, and seller/city visibility.

---

## What Admin Can Do

### Browse and filter warehouses

- search by warehouse name, address, city, or manager name
- filter by:
  - active/inactive
  - visible to seller dashboard
  - created date range

### Create and update warehouse

Warehouse form fields:

- name
- address
- city
- managers
- active status
- visible on seller dashboard
- delivery company (optional)

### Assign warehouse managers

- selected managers must not already manage another warehouse
- on create/update, user `managedWarehouseId` is updated accordingly

### Delete warehouse (with guard)

Deletion is blocked if:

- warehouse still has stock quantity > 0
- warehouse has related orders

---

## Delivery Company Linking

A warehouse can be linked to one delivery company.

Rules:

- linked company must exist
- linked company must be active

When linked, the warehouse can use that company delivery-fee cities.

---

## City Visibility in Edit Warehouse Sheet

Inside **Update Warehouse** sheet, admin can manage city visibility for that warehouse.

### How it works

- cities are loaded from delivery fees of the linked delivery company
- each city has a visibility flag per warehouse
- default behavior: if no warehouse-city row exists yet, city is treated as visible

### Admin controls

- toggle visibility per city
- search cities
- bulk actions: **Show all** / **Hide all**

### Effect

Hidden cities do not appear in the order city selector for that warehouse.

---

## Permissions

- View warehouses: `warehouses:view`
- Manage warehouses: `warehouses:manage`
- Some delivery/company visibility actions also allow: `settings:manage`
