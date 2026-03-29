# Product Variants

## Overview

The **Product Variants** page manages reusable product variant templates - combinations of colors, sizes, and custom types that can be assigned to products.

!!! tip "Reusable Templates"
Product variants are pre-configured combinations that save time when creating similar products.

---

## Purpose

This page helps you:

- ✅ **Create variant templates** for product types
- ✅ **Combine colors and sizes** into variant sets
- ✅ **Add custom type values** to templates
- ✅ **Reuse templates** across multiple products
- ✅ **Manage variant inventory** efficiently
- ✅ **Standardize product creation** across catalog

---

## What You'll See

### Page Header

!!! info "Template Management"
Create and manage product variant templates for efficient product creation.

**Header Content:**

| Element           | Description                                 |
| ----------------- | ------------------------------------------- |
| **Title**         | "Product Variants"                          |
| **Description**   | "Manage reusable product variant templates" |
| **Create Button** | "Create Product Variant"                    |

### Template Table

A comprehensive table showing all product variant templates:

| Field             | Description             | What It Shows                       |
| ----------------- | ----------------------- | ----------------------------------- |
| **Template Name** | Display name            | Human-readable template identifier  |
| **Variant Type**  | Template type           | COLOR_SIZE or CUSTOM                |
| **Product Count** | Usage count             | How many products use this template |
| **Created Date**  | When template was added | Track template creation             |
| **Updated Date**  | Last modification       | Track template changes              |
| **Actions**       | Edit/Delete buttons     | Quick access to modify or remove    |

### Template Details (Expanded View)

!!! success "Complete Information"
Click on a template to see and edit its full variant configuration.

**Expanded Template Details:**

| Field                 | Description                                     |
| --------------------- | ----------------------------------------------- |
| **Colors**            | Selected color variants for this template       |
| **Sizes**             | Selected size variants for this template        |
| **Custom Types**      | Selected custom type variants for this template |
| **Variants Preview**  | Visual preview of all combinations              |
| **Template Settings** | Sort order, display options                     |

---

## How to Use This Page

### Creating Product Variant Templates

!!! tip "Time-Saving Templates"
Create templates once, reuse across many products.

**Steps:**

1. **Click** "Create Product Variant" button
2. **Choose variant type**:
   - **COLOR_SIZE**: For products with color and size combinations
   - **CUSTOM**: For products with custom type options
3. **Select variants**:
   - For COLOR_SIZE: Choose colors and sizes
   - For CUSTOM: Choose custom types and values
4. **Set template name**: Give template a descriptive name
5. **Click** "Save" to create template

!!! example "T-Shirt Template Creation"
Creating a product variant template for t-shirts.

**Template Example:**

```
Template Name: "Basic T-Shirt Collection"
Variant Type: COLOR_SIZE

Selected Colors:
  - Red
  - Blue
  - Green
  - Black
  - White

Selected Sizes:
  - Small
  - Medium
  - Large
  - XL

Generated Variants:
  - Red-Small
  - Red-Medium
  - Red-Large
  - Red-XL
  - Blue-Small
  - Blue-Medium
  - Blue-Large
  - Blue-XL
  - Green-Small
  - Green-Medium
  - Green-Large
  - Green-XL
  - Black-Small
  - Black-Medium
  - Black-Large
  - Black-XL
  - White-Small
  - White-Medium
  - White-Large
  - White-XL

Total: 20 variants
```

### Creating Custom Type Templates

!!! success "Flexible Customization"
Custom type templates enable any product variation you need.

**Steps:**

1. **Select "CUSTOM" as variant type**
2. **Choose custom type**: Material, Length, Style, etc.
3. **Add type values**: Define the options for this type
4. **Set template name**: Give template a descriptive name
5. **Click** "Save" to create template

!!! example "Furniture Template Creation"
Creating a product variant template for furniture.

**Template Example:**

```
Template Name: "Oak Furniture Collection"
Variant Type: CUSTOM

Custom Type: Material
Type Values:
  - Oak
  - Pine
  - Walnut
  - Mahogany

Generated Variants:
  - Oak
  - Pine
  - Walnut
  - Mahogany

Total: 4 variants
```

### Editing Templates

!!! info "Quick Updates"
Modify template variants as your catalog evolves.

**Steps:**

1. **Click** "Edit" button on template row
2. **Modify variant selections**:
   - Add or remove colors/sizes/custom types
   - Change template name
   - Adjust display order
3. **Click** "Save" to apply changes

!!! warning "Product Impact"
Changing a template affects all products that use it. Consider carefully!

### Deleting Templates

!!! danger "Check Usage First"
Deleting a template removes it from available options.

**Before Deleting:**

| Check                        | Why It Matters                            |
| ---------------------------- | ----------------------------------------- |
| ✅ **Check product usage**   | How many products use this template?      |
| ✅ **Review variant needs**  | Do other products need similar templates? |
| ✅ **Consider replacements** | Create new template before deleting       |
| ✅ **Plan migration**        | Migrate affected products to new template |

**Deletion Impact:**

| Impact                      | What Happens                         |
| --------------------------- | ------------------------------------ |
| **Template removed**        | Template no longer available         |
| **Products affected**       | Products lose this template option   |
| **Future product creation** | Can't reuse this template anymore    |
| **Variant options lost**    | All configured combinations are lost |

---

## Template Architecture

### Template Types

!!! info "Two Main Types"
Product variants support two main variant approaches.

| Type           | Description                 | Best For                                     |
| -------------- | --------------------------- | -------------------------------------------- |
| **COLOR_SIZE** | Color and size combinations | Fashion, apparel, shoes                      |
| **CUSTOM**     | Custom type options         | Furniture, electronics, specialized products |

### COLOR_SIZE Templates

!!! success "Combinatorial Approach"
COLOR_SIZE templates create all color × size combinations.

**Template Structure:**

```
COLOR_SIZE Template:
├── Template Name
├── Colors Array
│   ├── Color 1
│   ├── Color 2
│   └── Color N
├── Sizes Array
│   ├── Size 1
│   ├── Size 2
│   └── Size M
└── Generated Variants = All (Color × Size) combinations
```

**Variant Generation:**

```
Colors: [Red, Blue, Green]
Sizes: [Small, Medium, Large]

Generated Variants:
  Red-Small
  Red-Medium
  Red-Large
  Blue-Small
  Blue-Medium
  Blue-Large
  Green-Small
  Green-Medium
  Green-Large

Total: 9 variants (3 × 3)
```

### CUSTOM Templates

!!! tip "Type-Based Approach"
CUSTOM templates group variant options by type.

**Template Structure:**

```
CUSTOM Template:
├── Template Name
├── Custom Type
│   └── Type Name (e.g., Material, Length)
├── Type Values Array
│   ├── Value 1
│   ├── Value 2
│   └── Value N
└── Generated Variants = Type values
```

**Variant Generation:**

```
Custom Type: Material
Type Values: [Oak, Pine, Walnut, Mahogany]

Generated Variants:
  Oak
  Pine
  Walnut
  Mahogany

Total: 4 variants
```

---

## Best Practices

### Template Planning

!!! tip "Think Ahead"
Plan your variant templates before creating them.

**Planning Steps:**

1. **Analyze your product catalog** - What product types do you have?
2. **Identify common patterns** - Which variants are repeated?
3. **Create templates for patterns** - Group repeated variants into templates
4. **Use descriptive names** - Make templates easy to identify
5. **Consider future products** - Will new products fit existing templates?

### Template Naming

!!! success "Clear Identification"
Good template names make templates easy to find and use.

**Naming Guidelines:**

| Guideline                       | Example                               | Why It Matters     |
| ------------------------------- | ------------------------------------- | ------------------ |
| ✅ **Include product type**     | "Basic T-Shirt" vs "T-Shirt"          | Easy to identify   |
| ✅ **Include key attributes**   | "Red-Blue Collection" vs "Basic"      | Describes variants |
| ✅ **Use consistent naming**    | "Standard T-Shirt", "Premium T-Shirt" | Shows relationship |
| ✅ **Keep names short**         | "Red XL" vs "Extra Large Red Color"   | Easy to scan       |
| ✅ **Avoid special characters** | "Red T-Shirt" vs "Red_T-Shirt"        | Cleaner display    |

**Naming Examples:**

```
Good:
- Basic T-Shirt Collection
- Premium T-Shirt Set
- Summer Color Palette
- Standard Sizes Set
- Oak Furniture Line

Avoid:
- Template 1
- Variant Set A
- Basic T's
- Red_T-Shirt
- Summer-Palette
```

### COLOR_SIZE Template Design

!!! info "Balanced Combinations"
Create practical and manageable color × size combinations.

**Design Principles:**

| Principle                          | Description                                     | Example                          |
| ---------------------------------- | ----------------------------------------------- | -------------------------------- |
| ✅ **Core colors only**            | Use essential colors, not every shade           | Red, Blue, Black, White          |
| ✅ **Practical sizes**             | Focus on most common sizes                      | S, M, L, XL                      |
| ✅ **Avoid too many combinations** | Keep templates manageable                       | 20-30 variants max               |
| ✅ **Consider costs**              | Too many variants increase inventory complexity | Fewer colors/sizes = lower costs |

**Optimal Template Size:**

| Template          | Colors   | Sizes   | Variants | Complexity      |
| ----------------- | -------- | ------- | -------- | --------------- |
| **Minimal**       | 3 colors | 3 sizes | 9        | Low complexity  |
| **Standard**      | 5 colors | 4 sizes | 20       | Balanced        |
| **Comprehensive** | 8 colors | 5 sizes | 40       | High complexity |

### CUSTOM Template Design

!!! tip "Product-Specific Options\*\*
Design custom type templates around actual product needs.

**Design Principles:**

| Principle                        | Description                            | Example                 |
| -------------------------------- | -------------------------------------- | ----------------------- |
| ✅ **Product-relevant types**    | Match types to product characteristics | Furniture → Material    |
| ✅ **Clear type values**         | Use specific, recognizable values      | Oak, Pine, Walnut       |
| ✅ **Mutually exclusive values** | Each option should be distinct         | Colors vs. patterns     |
| ✅ **Consider future options**   | Leave room for expansion               | Basic + premium options |

**Custom Type Examples:**

```
Furniture:
  Custom Type: Material
  Type Values: [Oak, Pine, Walnut, Mahogany]

Electronics:
  Custom Type: Storage Capacity
  Type Values: [64GB, 128GB, 256GB, 512GB, 1TB]

Bedding:
  Custom Type: Size
  Type Values: [Twin, Full, Queen, King, California King]
```

---

## Common Use Cases

### Scenario 1: Create Basic Product Template

!!! example "Standard T-Shirt Template"
Creating a basic template for t-shirt products.

**Workflow:**

```
[Identify Requirements]
    ↓
"Standard t-shirts - Core colors, standard sizes"
    ↓
[Select Variant Type]
    ↓
COLOR_SIZE
    ↓
[Choose Colors]
    ↓
Red, Blue, Black, White
    ↓
[Choose Sizes]
    ↓
S, M, L, XL
    ↓
[Set Template Name]
    ↓
"Basic T-Shirt Collection"
    ↓
[Create Template]
    ↓
20 variants generated
    ↓
[Use for Products]
    ↓
Assign template when creating t-shirts
```

**Outcome:**

- ✅ Reusable template
- ✅ 20 variant combinations
- ✅ Efficient product creation
- ✅ Consistent catalog

### Scenario 2: Create Seasonal Color Template

!!! success "Seasonal Collections"
Create templates for seasonal product collections.

**Workflow:**

```
[Plan Seasonal Collection]
    ↓
"Summer 2024 - Bright, fresh colors"
    ↓
[Select Summer Colors]
    ↓
Coral, Mint, Yellow, Light Blue
    ↓
[Reuse Standard Sizes]
    ↓
S, M, L, XL
    ↓
[Set Template Name]
    ↓
"Summer 2024 T-Shirt Palette"
    ↓
[Create Template]
    ↓
4 colors × 4 sizes = 16 variants
    ↓
[Create Summer Products]
    ↓
Assign summer template to summer products
```

**Outcome:**

- ✅ Seasonal variety
- ✅ Consistent size range
- ✅ Marketing opportunities
- ✅ Organized catalog

### Scenario 3: Create Furniture Template

!!! tip "Material Templates"
Furniture products often vary by material. Create material-specific templates.

**Workflow:**

```
[Identify Furniture Line]
    ↓
"Dining tables - Multiple wood types"
    ↓
[Select Variant Type]
    ↓
CUSTOM
    ↓
[Choose Custom Type]
    ↓
"Material"
    ↓
[Add Type Values]
    ↓
Oak, Pine, Walnut, Mahogany
    ↓
[Set Template Name]
    ↓
"Wooden Furniture Materials"
    ↓
[Create Template]
    ↓
4 variants
    ↓
[Use for Furniture Products]
    ↓
Assign material template to table products
```

**Outcome:**

- ✅ Material-specific options
- ✅ Clear product differences
- ✅ Easy material selection
- ✅ Professional catalog

---

## Troubleshooting

### Template Not Showing in Product Form

!!! warning "Availability Issue"
If a template doesn't appear, check its status.

| Possible Cause               | Solution                                           |
| ---------------------------- | -------------------------------------------------- |
| **Template not active**      | Make sure template is active/visible               |
| **Wrong variant type**       | Check if product's variant type matches template   |
| **Template has no variants** | Add at least one variant to template               |
| **Cache delay**              | Refresh the product creation page                  |
| **Permission issue**         | Verify you have `product-variants:view` permission |

### Too Many Variants Generated

!!! danger "Complexity Warning"
Too many variants make products hard to manage.

**Symptoms:**

- Products have 50+ variants
- Slow product creation
- Difficult inventory management
- Customer confusion

**Solutions:**

| Solution                             | Description                 |
| ------------------------------------ | --------------------------- |
| ✅ **Reduce colors**                 | Use fewer core colors       |
| ✅ **Reduce sizes**                  | Focus on common sizes       |
| ✅ **Split into multiple templates** | Basic, Premium, Seasonal    |
| ✅ **Use templates selectively**     | Don't apply to all products |
| ✅ **Review variant usage**          | Remove unused variants      |

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

- 📦 Learn about [Variants](./variants.md)
- 📋 Learn about [Categories](./categories/categories.md)
- 📦 Learn about [Product List](../product/product-list.md)
