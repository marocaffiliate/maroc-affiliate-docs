# Categories Management

## Overview

The **Categories** page is your central hub for managing product categories across the entire marocAffiliate platform.

> **Tip**: Categories organize products into logical groups, making it easier for sellers to browse and find what they need.

---

## What You Can Do

### Create Categories

1. Click **Create Category** button
2. Enter category details:
   - **Name**: Human-readable name (e.g., "Clothing")
   - **Slug**: URL-friendly identifier (e.g., "clothing")
   - **Description**: Additional information
3. Click **Save** to create category

> **Note**: Keep slugs lowercase and use hyphens instead of spaces.

### Edit Categories

1. Click **Edit** button on category row
2. Update category details
3. Click **Save** to apply changes

> **Warning**: Changing a category's slug affects all products in that category. Use caution!

### Delete Categories

1. Click **Delete** button on category row
2. Confirm deletion

> **Danger**: Deleting a category removes it and all associated data. Be certain!

> **Best Practice**: Don't delete categories that have products. Create a replacement first, then migrate products.

### Filter Categories

| Option          | How It Works                   | When to Use                     |
| --------------- | ------------------------------ | ------------------------------- |
| **Name search** | Searches category names        | Find category by name           |
| **Slug search** | Searches slug field            | Find category by URL identifier |
| **Date range**  | Filter by creation/update date | Find recent or old categories   |

### Sort Categories

Click column headers to sort:

- **Name** - Alphabetical order
- **Created Date** - Newest first
- **Updated Date** - Most recently modified first
- **Product Count** - Most or fewest products

---

## Best Practices

### Naming Conventions

| Do                                | Don't                                                   |
| --------------------------------- | ------------------------------------------------------- |
| ✅ Use clear, descriptive names   | ❌ Use abbreviations (e.g., "Mens" vs "Men's")          |
| ✅ Use standard terminology       | ❌ Use jargon (e.g., "Apparel" vs "Clothing")           |
| ✅ Keep names short and memorable | ❌ Use long, complex names                              |
| ✅ Use consistent capitalization  | ❌ Mix capitalization (e.g., "Clothing", "ELECTRONICS") |

### Slug Guidelines

| Guideline                | Example             | Why It Matters           |
| ------------------------ | ------------------- | ------------------------ |
| ✅ Lowercase only        | `mens-shirts`       | Consistent URLs          |
| ✅ Use hyphens           | `summer-collection` | Better than underscores  |
| ✅ No special characters | `clothing`          | Clean URLs               |
| ✅ Keep it short         | `dresses`           | Easier to type and share |


---

## Permissions

| Action            | Required Permission |
| ----------------- | ------------------- |
| View categories   | `categories:view`   |
| Create categories | `categories:create` |
| Edit categories   | `categories:edit`   |
| Delete categories | `categories:delete` |

---

## Next Steps

- 🎨 Learn about [Variants](./variants.md)
- 🏷️ Learn about [Product Variants](./product-variants.md)
- 📦 Learn about [Product List](../product/product-list.md)
