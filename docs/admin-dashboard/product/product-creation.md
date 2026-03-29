# Product Creation Page

## Overview

Add new products to your catalog with all required information.

---

## Fill Out Form

### Basic Information

| Field            | Description                     | Required             |
| ---------------- | ------------------------------- | -------------------- |
| **Product Name** | Clear, descriptive name         | ✅                   |
| **Provider**     | Select from available suppliers | ✅                   |
| **Category**     | Product category                | ✅                   |
| **Rating**       | Quality rating (0-5 stars)      | ✅                   |
| **Description**  | Product details                 | Use rich text editor |

> **Note**: System automatically generates a unique product code.

### Pricing

| Field                      | Description                        | Required |
| -------------------------- | ---------------------------------- | -------- |
| **Buy Price**              | Your cost to acquire product       | ✅       |
| **Selling Price**          | Standard price for customers       | ✅       |
| **Old Price**              | Original price (for discounts)     | ⭕       |
| **POS Price**              | In-store price                     | ⭕       |
| **Warehouse Price**        | Internal price                     | ⭕       |
| **Special Seller Pricing** | Custom prices for specific sellers | ⭕       |

### Media

| Field      | Description           | Required          |
| ---------- | --------------------- | ----------------- |
| **Images** | Upload product images | ✅ (at least one) |
| **Video**  | Upload product video  | ⭕                |

### Settings

| Setting                 | Options             | Description           |
| ----------------------- | ------------------- | --------------------- |
| **Minimum Seller Type** | Who can see product | ✅                    |
| **Normal**              | All sellers         | Available to everyone |
| **Pro**                 | Pro and VIP sellers | Premium products      |
| **VIP**                 | Only VIP sellers    | Exclusive products    |

> **Tip**: Higher seller tiers can see products from lower tiers.

| Setting          | Options                   | Description          |
| ---------------- | ------------------------- | -------------------- |
| **Variant Type** | Product variant system    | ✅                   |
| **None**         | Single-SKU product        | Basic items          |
| **Color/Size**   | Color and size variations | Clothing, shoes      |
| **Custom**       | Custom variation types    | Specialized products |

| Setting            | Options               | Description        |
| ------------------ | --------------------- | ------------------ |
| **Public/Private** | Visibility scope      | ✅                 |
| **Public**         | All eligible sellers  | Standard products  |
| **Private**        | Selected sellers only | Exclusive products |

> **Note**: If Private, select specific sellers to grant access.

### Product Variants

Select and assign existing variants to your product.

> **Note**: Variants must be created first in the Variants page.

---

## Create Product

### Review

Before submitting, review all information:

- [ ] All required fields filled
- [ ] Prices are reasonable
- [ ] At least one image uploaded
- [ ] Variant selections make sense

### Submit

Click **Create Product** button to add product to your catalog.

> **Success**: The system validates and creates your product, making it available to eligible sellers.

---

## Permissions

| Action          | Required Permission |
| --------------- | ------------------- |
| Create products | `products:create`   |

---

## Next Steps

- 📋 Return to [Product List](./product-list.md) to view all products
- ✏️ Edit products on the [Product Edit](./product-edit.md) page
- 🏷️ View product details on the [Product Details](./product-details.md) page
