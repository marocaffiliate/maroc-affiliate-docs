# Product Variants

## Overview

The **Product Variants** page manages reusable product variant templates - combinations of colors, sizes, and custom types.

> **Tip**: Product variants are pre-configured combinations that save time when creating similar products.

---

## What You Can Do

### Create Product Variant Templates

1. Click **Create Product Variant** button
2. Choose variant type:
   - **COLOR_SIZE**: For products with color and size combinations
   - **CUSTOM**: For products with custom type options
3. Select variants:
   - For COLOR_SIZE: Choose colors and sizes
   - For CUSTOM: Choose custom types and values
4. Set template name: Give template a descriptive name
5. Click **Save** to create template

> **Example**: Creating a template for t-shirts with red, blue, green colors and small, medium, large sizes.

### Create Custom Type Templates

1. Select **CUSTOM** as variant type
2. Choose custom type: Material, Length, Style, etc.
3. Add type values: Define the options for this type
4. Set template name
5. Click **Save** to create template

> **Example**: Creating a template for furniture with different wood types.

### Edit Templates

1. Click **Edit** button on template row
2. Modify variant selections
3. Click **Save** to apply changes

> **Warning**: Changing a template affects all products that use it. Consider carefully!

### Delete Templates

1. Click **Delete** button on template row
2. Confirm deletion

> **Danger**: Deleting a template removes it from available options. Check usage first.

> **Best Practice**: Create new template before deleting. Migrate affected products to new template.

---

## Template Architecture

### Template Types

| Type           | Description                 | Best For                                     |
| -------------- | --------------------------- | -------------------------------------------- |
| **COLOR_SIZE** | Color and size combinations | Fashion, apparel, shoes                      |
| **CUSTOM**     | Custom type options         | Furniture, electronics, specialized products |

---

## Permissions

| Action                  | Required Permission       |
| ----------------------- | ------------------------- |
| View product variants   | `product-variants:view`   |
| Create product variants | `product-variants:create` |
| Edit product variants   | `product-variants:edit`   |
| Delete product variants | `product-variants:delete` |

---

## Next Steps

- 🎨 Learn about [Variants](./variants.md)
- 📋 Learn about [Categories](./categories/categories.md)
- 📦 Learn about [Product List](../product/product-list.md)
