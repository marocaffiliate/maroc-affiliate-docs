# Categories Management

## Overview

The **Categories** page is your central hub for managing product categories across the entire marocAffiliate platform.

!!! tip "Organized Products"
Categories organize products into logical groups, making it easier for sellers to browse and find what they need.

---

## Purpose

This page helps you:

- ✅ **Organize products** into logical groups (Clothing, Electronics, etc.)
- ✅ **Create categories** for new product types
- ✅ **Edit categories** to update names or descriptions
- ✅ **Delete categories** that are no longer needed
- ✅ **View product counts** per category
- ✅ **Filter products** by category throughout the platform

---

## What You'll See

### Main Table

A clean, organized table showing all categories:

| Field             | Description             | What It Shows                         |
| ----------------- | ----------------------- | ------------------------------------- |
| **Category Name** | Display name            | Human-readable category name          |
| **Slug**          | URL-friendly identifier | Used in URLs and API calls            |
| **Description**   | Category details        | Additional information about category |
| **Product Count** | Number of products      | How many products in this category    |
| **Created Date**  | When category was added | Track when category was created       |
| **Updated Date**  | Last modification       | Track when category was changed       |
| **Actions**       | Edit/Delete buttons     | Quick access to modify or remove      |

### Table Features

!!! info "Interactive Table"
The categories table supports common operations.

| Feature           | How It Works                 | Best For                 |
| ----------------- | ---------------------------- | ------------------------ |
| **Sorting**       | Click column headers to sort | Find categories quickly  |
| **Pagination**    | Navigate through pages       | Manage many categories   |
| **Search**        | Filter by name/slug          | Find specific categories |
| **Row Selection** | Select multiple categories   | Bulk operations          |

---

## How to Use This Page

### Creating Categories

!!! success "Easy Creation"
Add new categories anytime to expand your product catalog.

**Steps:**

1. **Click** "Create Category" button
2. **Enter category details**:
   - **Name**: Human-readable name (e.g., "Clothing")
   - **Slug**: URL-friendly identifier (e.g., "clothing")
   - **Description**: Additional information
3. **Click** "Save" to create category

!!! tip "Slug Best Practices" - Use lowercase letters - Use hyphens instead of spaces - Keep it short and descriptive - Example: "t-shirts" instead of "men-s-casual-shirts"

### Editing Categories

!!! info "Quick Updates"
Modify category information as your catalog evolves.

**Steps:**

1. **Click** "Edit" button on category row
2. **Update category details**:
   - Change name if needed
   - Update description
   - Modify slug if necessary (use caution!)
3. **Click** "Save" to apply changes

!!! warning "Slug Changes Impact Products"
Changing a category's slug affects all products in that category. Use caution!

### Deleting Categories

!!! danger "Permanent Action"
Deleting a category removes it and all associated data. Be certain!

**When You Delete:**

| What Happens          | Impact                                  |
| --------------------- | --------------------------------------- |
| **Category removed**  | Category no longer available            |
| **Products affected** | Products lose their category assignment |
| **Historical data**   | Past references may be broken           |

**Best Practice:**

- ✅ **Don't delete categories** if products exist
- ✅ **Create replacement first** then migrate products
- ✅ **Archive instead** if you might need it later
- ✅ **Check product associations** before deleting

### Filtering Categories

!!! tip "Find Categories Fast"
Use search to locate specific categories quickly.

**Search Options:**

| Option          | How It Works                   | When to Use                     |
| --------------- | ------------------------------ | ------------------------------- |
| **Name search** | Searches category names        | Find category by name           |
| **Slug search** | Searches slug field            | Find category by URL identifier |
| **Date range**  | Filter by creation/update date | Find recent or old categories   |

---

## Category Best Practices

### Naming Conventions

!!! success "Clear Names"
Consistent naming makes your catalog professional.

| Do                                    | Don't                                                   |
| ------------------------------------- | ------------------------------------------------------- |
| ✅ Use **clear, descriptive names**   | ❌ Use abbreviations (e.g., "Mens" vs "Men's")          |
| ✅ Use **standard terminology**       | ❌ Use jargon (e.g., "Apparel" vs "Clothing")           |
| ✅ Keep names **short and memorable** | ❌ Use long, complex names                              |
| ✅ Use **consistent capitalization**  | ❌ Mix capitalization (e.g., "Clothing", "ELECTRONICS") |

### Slug Guidelines

!!! tip "URL-Friendly Slugs"
Slugs become part of product URLs. Make them clean and consistent.

| Guideline                    | Example             | Why It Matters           |
| ---------------------------- | ------------------- | ------------------------ |
| ✅ **Lowercase only**        | `men-shirts`        | Consistent URLs          |
| ✅ **Use hyphens**           | `summer-collection` | Better than underscores  |
| ✅ **No special characters** | `clothing`          | Clean URLs               |
| ✅ **Keep it short**         | `dresses`           | Easier to type and share |
| ❌ **Avoid spaces**          | `men shirts`        | Use hyphens instead      |
| ❌ **Avoid numbers**         | `category-1`        | Less descriptive         |
| ❌ **Avoid underscores**     | `men_shirts`        | Hyphens are cleaner      |

### Category Structure

!!! info "Logical Organization"
Think about your catalog structure when creating categories.

**Good Examples:**

```
📦 Apparel
   ├── 👕 Men's Clothing
   ├── 👩 Women's Clothing
   ├── 👶 Kids' Clothing
   └── 👴 Accessories

📱 Electronics
   ├── 📱 Smartphones
   ├── 💻 Laptops
   ├── 🎧 Audio
   └── 🔌 Accessories

🏠 Home & Garden
   ├── 🛋 Furniture
   ├── 🍽 Kitchenware
   ├── 🌱 Garden Tools
   └── 🏡 Decor
```

**Categories to Consider:**

| Category              | Typical Subcategories               | Products                         |
| --------------------- | ----------------------------------- | -------------------------------- |
| **Clothing**          | Men's, Women's, Kids', Accessories  | T-shirts, jeans, dresses         |
| **Electronics**       | Phones, Laptops, Audio, Accessories | Smartphones, tablets, headphones |
| **Home & Garden**     | Furniture, Kitchen, Garden          | Tables, cookware, tools          |
| **Sports & Outdoors** | Equipment, Apparel                  | Balls, rackets, shoes            |
| **Books & Media**     | Books, Movies, Music                | Novels, DVDs, streaming          |

---

## Common Use Cases

### Scenario 1: Organize New Product Line

!!! example "Catalog Setup"
When adding new product types, create appropriate categories first.

**Workflow:**

```
[Identify New Product Type]
    ↓
"Summer 2024 Collection"
    ↓
[Create Parent Category]
    ↓
"Summer 2024"
    ↓
[Create Subcategories]
    ↓
"Men's Summer", "Women's Summer", "Kids' Summer"
    ↓
[Add Products to Categories]
    ↓
Assign each product to appropriate category
```

**Outcome:**

- ✅ Products organized logically
- ✅ Easy for sellers to browse
- ✅ Scalable structure
- ✅ Professional catalog

### Scenario 2: Clean Up Category Names

!!! tip "Consistency Matters"
Keep category names consistent across your entire catalog.

**Process:**

```
[Review All Categories]
    ↓
[List Inconsistent Names]
    ↓
"Clothing", "APPAREL", "Mens Wear"
    ↓
[Standardize Names]
    ↓
"Clothing", "Apparel", "Men's Apparel"
    ↓
[Update Each Category]
    ↓
Apply standard naming convention
```

**Outcome:**

- ✅ Professional appearance
- ✅ Better user experience
- ✅ Easier to maintain
- ✅ Consistent catalog

### Scenario 3: Add Category for New Season

!!! success "Seasonal Planning"
Create seasonal categories to highlight new arrivals.

**Workflow:**

```
[Plan Seasonal Categories]
    ↓
"Spring 2024", "Summer 2024", "Fall 2024", "Winter 2024"
    ↓
[Create Categories in Advance]
    ↓
Prepare before products arrive
    ↓
[Update Products as Season Arrives]
    ↓
Move products into seasonal categories
```

**Outcome:**

- ✅ Products highlighted by season
- ✅ Better marketing opportunities
- ✅ Sellers can promote seasonal items
- ✅ Organized inventory

---

## Troubleshooting

### Category Not Showing in Product Form

!!! warning "Sync Issues"
If a newly created category doesn't appear, it might be a caching issue.

| Possible Cause          | Solution                                       |
| ----------------------- | ---------------------------------------------- |
| **Cache delay**         | Refresh the product creation page              |
| **Permission issue**    | Verify you have `categories:create` permission |
| **Category not active** | Ensure category is active/visible              |
| **Network issue**       | Check internet connection and try again        |

### Can't Delete Category

!!! danger "Protected Data"
Some categories cannot be deleted due to business rules.

| Situation                | Reason                       | Solution                         |
| ------------------------ | ---------------------------- | -------------------------------- |
| **Has products**         | Category contains products   | Move products first, then delete |
| **System category**      | Protected default category   | Cannot delete system categories  |
| **Referenced elsewhere** | Used in orders or promotions | Remove references first          |

### Slug Already Exists

!!! info "Unique Requirements"
Slugs must be unique across all categories.

**Solution:**

1. **Choose a different slug** for the category
2. **Add qualifiers** if needed:
   - Instead of: `shirts`
   - Use: `t-shirts` or `men-shirts`
3. **Add year or season** if appropriate:
   - Instead of: `summer`
   - Use: `summer-2024` or `summer-collection`

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

- 📋 Learn about [Variants](./variants.md)
- 🏷️ Learn about [Product Variants](./product-variants.md)
- 📦 Learn about [Product List](../product/product-list.md)
