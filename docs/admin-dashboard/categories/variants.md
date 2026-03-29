# Variants Management

## Overview

The **Variants** page is your control center for managing product variant types - Colors, Sizes, and Custom Variants.

> **Tip**: Variants (colors, sizes, custom types) are reusable components that can be combined when creating products.

---

## What You Can Do

### Create Color Variants

1. Click **Colors** tab (🎨)
2. Click **Create Variant** button
3. Enter color details:
   - **Name**: Color name (e.g., "Red", "Navy Blue")
   - **Hex Code**: Color code (e.g., "#FF0000", "#000080")
   - **Sort Order**: Display position
4. Click **Save** to create color

> **Best Practice**: Use standard color names and accurate hex codes.



### Create Size Variants

1. Click **Sizes** tab (📏)
2. Click **Create Variant** button
3. Enter size details:
   - **Name**: Size name (e.g., "Small", "Medium", "Large")
   - **Sort Order**: Display position
4. Click **Save** to create size

> **Best Practice**: Use industry-standard sizing and descriptive names.



### Create Custom Variant Types

1. Click **Custom Types** tab (🏷️)
2. Click **Create Variant** button
3. Enter custom type details:
   - **Name**: Type name (e.g., "Material", "Length", "Style")
   - **Sort Order**: Display position
4. Click **Save** to create custom type

> **Best Practice**: Use clear, descriptive names that match your products.



### Edit Variants

1. Click **Edit** button on variant row
2. Update variant details
3. Click **Save** to apply changes

> **Warning**: Changing sort order affects how variants appear in product forms. Test changes carefully!

### Delete Variants

1. Click **Delete** button on variant row
2. Confirm deletion

> **Danger**: Deleting variants affects products that use them. Review usage before deleting.

> **Best Practice**: Don't delete variants with active products. Keep old variants inactive instead of deleting.

### Filter and Sort Variants

| Feature           | How It Works                    |
| ----------------- | ------------------------------- |
| **Category Tabs** | Colors, Sizes, Custom Types     |
| **Search**        | Filter by variant name          |
| **Sorting**       | Sort by name, category, or date |
| **Pagination**    | Navigate through many variants  |

---

## Variant Architecture

### How Variants Work Together

Variants work together to create product variations.

**Variant Combination Flow:**

```
[Choose Variant Type]
    ↓
"COLOR_SIZE" or "CUSTOM"
    ↓
    ↓
┌─────────────────────────────────┐
│  COLOR_SIZE Variant             │
│  ┌─────────┐   ┌─────────┐      │
│  │ Colors  │   │  Sizes  │      │
│  └─────────┘   └─────────┘      │
│  Product Variants =             │
│   color × size combinations     │
│                                 │
└─────────────────────────────────┘
```

**Example: T-Shirt Product**

```
Color Variants: [Red, Blue, Green]
Size Variants: [S, M, L, XL]

Product Variants Created:
- Red-Small
- Red-Medium
- Red-Large
- Red-XLarge
- Blue-Small
- Blue-Medium
- Blue-Large
- Blue-XLarge
- Green-Small
- Green-Medium
- Green-Large
- Green-XLarge

Total: 12 variants
```

### Category Hierarchy

Variants are organized into three main categories:

| Category      | Purpose                  | Example Variants                       |
| ------------- | ------------------------ | -------------------------------------- |
| **🎨 Colors** | Color options            | Red, Blue, Green, Yellow, Black, White |
| **📏 Sizes**  | Size options             | XS, S, M, L, XL, XXL                   |
| **🏷️ Custom** | Product-specific options | Material, Length, Style, Pattern       |

---

## Permissions

| Action          | Required Permission |
| --------------- | ------------------- |
| View variants   | `variants:view`     |
| Create variants | `variants:create`   |
| Edit variants   | `variants:edit`     |
| Delete variants | `variants:delete`   |

---

## Next Steps

- 📦 Learn about [Categories](./categories/categories.md)
- 🏷️ Learn about [Product Variants](./product-variants.md)
- 📦 Learn about [Product List](../product/product-list.md)
