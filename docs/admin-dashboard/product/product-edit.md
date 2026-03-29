# Product Edit Page

## Overview

Modify existing products while protecting important business data.

---

## Business Restrictions

Some product information is protected based on business rules.

### What Gets Locked

| Field            | When Locked                 | Why                            |
| ---------------- | --------------------------- | ------------------------------ |
| **Product Code** | Product has customer orders | Orders reference product codes |
| **Variant Type** | Product has customer orders | Orders reference variant types |

Locked fields show a **Protected** badge and are disabled.

### What Shows Warnings

| Field                     | When Warning                    | Why                                                |
| ------------------------- | ------------------------------- | -------------------------------------------------- |
| **Price Changes**         | Product has purchase orders     | Price changes affect historical financial analysis |
| **Stock/Variant Changes** | Product has inventory movements | Changes affect inventory history                   |

> **Note**: A warning banner appears at the top of the page when restrictions apply.

---

## What You Can Edit

### Basic Information

| Field            | Editable                  |
| ---------------- | ------------------------- |
| **Product Name** | ✅ Always                 |
| **Provider**     | ✅ Always                 |
| **Category**     | ✅ Always                 |
| **Product Code** | 🔒 Locked if orders exist |
| **Variant Type** | 🔒 Locked if orders exist |
| **Rating**       | ✅ Always                 |

### Pricing

All price fields are editable but may show warnings.

| Field                      | Editable | Warning When  |
| -------------------------- | -------- | ------------- |
| **Buy Price**              | ✅       | Has purchases |
| **Selling Price**          | ✅       | Has purchases |
| **Old Price**              | ✅       | Always        |
| **POS Price**              | ✅       | Has purchases |
| **Warehouse Price**        | ✅       | Has purchases |
| **Special Seller Pricing** | ✅       | Always        |

### Media

| Field      | Editable  |
| ---------- | --------- |
| **Images** | ✅ Always |
| **Video**  | ✅ Always |

### Product Description

| Field           | Editable  |
| --------------- | --------- |
| **Description** | ✅ Always |

### Access Control

| Field                   | Editable      |
| ----------------------- | ------------- |
| **Minimum Seller Type** | ✅ Always     |
| **Public/Private**      | ✅ Always     |
| **Allowed Sellers**     | ✅ If Private |

### Variant Management

- **Add variants** - Assign new variant combinations
- **Remove variants** - Remove existing variant assignments
- **Manage stock** - Update stock levels per variant
- **Update pricing** - Set variant-specific prices

---

## Saving Changes

### Edit Product

1. Click the **Edit** button on the page
2. Make your changes
3. Click **Save** to apply changes

> **Success**: The system validates and applies your changes immediately.

---

## Permissions

| Action        | Required Permission |
| ------------- | ------------------- |
| View products | `products:view`     |
| Edit products | `products:edit`     |

---

## Next Steps

- 📋 Return to [Product List](./product-list.md) to view all products
- 📦 Create new products on the [Product Creation](./product-creation.md) page
- 🏷️ View product details on the [Product Details](./product-details.md) page
