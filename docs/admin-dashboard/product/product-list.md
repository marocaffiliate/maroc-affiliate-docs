# Product List Page

## Overview

View, search, filter, and manage all products in your catalog.

---

## What You Can Do

### Find Products

Use the search bar to find products by name, code, or description.

### Filter Products

| Filter             | Options                          |
| ------------------ | -------------------------------- |
| **Status**         | Available, Out of Stock, Draft   |
| **Category**       | Product categories               |
| **Variant Type**   | None, Color/Size, Custom         |
| **Seller Type**    | Normal, Pro, VIP                 |
| **Public/Private** | All sellers vs. specific sellers |
| **Date Range**     | Creation date range              |

### Sort Products

Click any column header to sort ascending or descending.

| Column              | Description          |
| ------------------- | -------------------- |
| **Name**            | Sort alphabetically  |
| **Code**            | Sort by product ID   |
| **Status**          | Sort by availability |
| **Selling Price**   | Sort by price        |
| **Created/Updated** | Sort by date         |

### Select Products

Click checkboxes to select individual products or use "Select All" to select all visible products. Selection persists across page changes.

### Take Actions

| Action           | Description              |
| ---------------- | ------------------------ | -------------------------------------- |
| **View Details** | Click product name       | See complete product information       |
| **Edit**         | Click Edit button        | Modify product information             |
| **Delete**       | Click Delete button      | Remove product (requires confirmation) |
| **Bulk Delete**  | Select multiple products | Delete all at once                     |

---

## Product Status

| Status              | Meaning                                      |
| ------------------- | -------------------------------------------- |
| 🟢 **Available**    | In stock and ready to sell                   |
| 🔴 **Out of Stock** | No inventory, sellers can view but not order |
| 🟡 **Draft**        | Not published, only admins can see           |

---

## Permissions

| Action          | Required Permission |
| --------------- | ------------------- |
| View products   | `products:view`     |
| Create products | `products:create`   |
| Edit products   | `products:edit`     |
| Delete products | `products:delete`   |

---

## Next Steps

- 📦 Create new products on the [Product Creation](./product-creation.md) page
- ✏️ Edit products on the [Product Edit](./product-edit.md) page
- 🏷️ View product details on the [Product Details](./product-details.md) page
