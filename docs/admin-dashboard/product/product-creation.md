# Product Creation Page

## Overview

The **Product Creation page** is where you add new products to marocAffiliate platform. This is your starting point for getting any product into your inventory and making it available to sellers.

!!! tip "First Step"
Every product starts here. Complete information correctly now to save time later.

---

## Purpose

This page helps you:

- ✅ **Create new products** with all necessary information
- ✅ **Set up pricing** across different sales channels
- ✅ **Upload product images** and videos
- ✅ **Configure who can see** and sell your product
- ✅ **Associate product variants** (colors, sizes, etc.)
- ✅ **Make products available** to sellers

---

## What You'll Fill Out

### Step 1: Basic Information

!!! info "Product Identity"
These fields define what your product is and where it comes from.

| Field            | Description                     | Tips                                                         |
| ---------------- | ------------------------------- | ------------------------------------------------------------ |
| **Product Name** | Clear, descriptive product name | Keep it concise but informative; use standard terminology    |
| **Provider**     | Who provides this product       | Choose from registered suppliers; this tracks product origin |
| **Category**     | Product category classification | Organizes products; helps sellers browse catalog             |
| **Rating**       | Quality rating (0-5 stars)      | Helps sellers and customers understand product quality       |
| **Description**  | Detailed product description    | Use rich text editor for formatting; include key features    |

!!! success "Auto-Generated Code"
The system automatically generates a unique product code based on the name. You don't need to create one manually.

**Code Format:**

```
{PRODUCT-NAME}-{TIMESTAMP}

Example: TSHIRT-ABC123
```

### Step 2: Pricing

!!! warning "Pricing Strategy"
Carefully consider all your pricing channels. Each serves a different purpose.

| Field               | Description                             | Business Impact                                   |
| ------------------- | --------------------------------------- | ------------------------------------------------- |
| **Buy Price**       | How much you pay to acquire product     | Cost basis for profit calculations                |
| **Selling Price**   | How much sellers (and customers) pay    | Should include your profit margin                 |
| **Old Price**       | Original price before discount          | Creates sale effect, increases perceived value    |
| **POS Price**       | Price for in-store POS systems          | Different from online if you have physical stores |
| **Warehouse Price** | Internal price for inventory management | Not visible to sellers; used for accounting       |

#### Special Seller Pricing

!!! example "Wholesale Pricing"
Set custom prices for specific sellers for wholesale arrangements or special partnerships.

**How It Works:**

1. **Select seller** from dropdown
2. **Enter custom price** for that seller
3. **Click "Add"** to add to list
4. **Repeat** for multiple sellers
5. **Remove** entries by clicking X button

**Use Cases:**

- 💼 Wholesale pricing for bulk buyers
- 🤝 Special partner pricing
- 📊 Market-specific pricing
- 🎯 Strategic seller incentives

### Step 3: Media (Images & Video)

!!! tip "Visual Quality Matters"
High-quality images and videos significantly increase seller confidence and conversion rates.

#### Images

| Best Practice                           | Why It Matters                  |
| --------------------------------------- | ------------------------------- |
| Use **high-quality**, well-lit photos   | Professional appearance         |
| Show **product from multiple angles**   | Complete product understanding  |
| Include **lifestyle shots** if relevant | Context and usage               |
| Maintain **consistent image sizes**     | Professional catalog appearance |
| Use **transparent backgrounds**         | Clean look, easier integration  |

**Image Management:**

- **Drag and drop** images or click to select files
- **Upload as many** as needed (at least one required)
- **Reorder images** by dragging them
- **Remove images** by clicking X button

#### Video

!!! note "Optional But Powerful"
Videos are great for complex products but not required.

**Video Benefits:**

- 🎬 Shows **how product works**
- 🎯 Demonstrates **features in action**
- 📺 Reduces **returns** (customers see what they're getting)
- 🎨 Enhances **brand perception**

**Video Guidelines:**

- Use **MP4 or WEBM** format
- Keep file size **under 100MB** for faster loading
- Show **clear, well-lit** demonstrations
- Include **close-ups** of important features

### Step 4: Settings

!!! info "Access Control"
These settings determine who can see and order your product.

| Setting                 | Description                          | Impact                               |
| ----------------------- | ------------------------------------ | ------------------------------------ |
| **Minimum Seller Type** | Who can see this product             | Controls access by seller tier       |
| **Variant Type**        | How product variations are organized | Affects inventory tracking structure |
| **Public/Private**      | Visibility scope                     | Determines which sellers can view    |
| **Allowed Sellers**     | Specific sellers (if Private)        | Direct access control                |

#### Minimum Seller Type Options

!!! tip "Hierarchical Access"
Seller types follow a **hierarchical system** where higher tiers include lower tiers. Pro sellers can see Normal products, and VIP sellers can see both Normal and Pro products.

| Type       | Who Can See                      | Best For                       |
| ---------- | -------------------------------- | ------------------------------ |
| **Normal** | All sellers (Normal + Pro + VIP) | Standard products              |
| **Pro**    | Pro and VIP sellers              | Premium products               |
| **VIP**    | Only VIP sellers                 | Exclusive, high-value products |

**How It Works:**

```
VIP Seller → Can See: Normal + Pro + VIP Products
    ↓
Pro Seller → Can See: Normal + Pro Products (not VIP)
    ↓
Normal Seller → Can See: Normal Products Only
```

#### Variant Type Options

| Type           | Description                           | Example Products          |
| -------------- | ------------------------------------- | ------------------------- |
| **None**       | Single-SKU product (no variations)    | Basic items, accessories  |
| **Color/Size** | Product has color and size variations | T-shirts, shoes, clothing |
| **Custom**     | Product has custom variation types    | Specialized products      |

#### Public vs Private

!!! example "Visibility Strategy"
Choose visibility based on your product strategy and seller relationships.

| Setting     | Who Can See           | When to Use                              |
| ----------- | --------------------- | ---------------------------------------- |
| **Public**  | All eligible sellers  | Standard products, wide distribution     |
| **Private** | Only selected sellers | Exclusive products, limited availability |

**Private Product Selection:**

- Use **multi-select** to choose sellers
- Only **selected sellers** will see product
- Useful for **exclusive products** or **special arrangements**

### Step 5: Product Variants

!!! tip "Variant Basics"
Variants are different versions of the same product. They enable accurate inventory tracking.

#### What Are Variants?

| Variant Type   | Description                             | Example                               |
| -------------- | --------------------------------------- | ------------------------------------- |
| **Color/Size** | Product variations by color and size    | Red-Large, Blue-Small, Green-Medium   |
| **Custom**     | Product variations by custom attributes | Cotton-Medium, Wool-Large, Silk-Small |
| **None**       | Single-SKU product (no variations)      | Basic items with no variants          |

#### Why Use Variants?

!!! success "Inventory Benefits"
Variants enable accurate inventory tracking and detailed sales reporting.

**Benefits:**

- ✅ **Accurate inventory tracking** per variation
- ✅ **Detailed sales reporting** by color, size, etc.
- ✅ **Helps sellers choose** specific versions
- ✅ **Reduces overstock/understock** issues

#### How to Assign Variants

**Step-by-Step:**

1. **Select variant type** (None/Color/Size/Custom)
2. **Click refresh button** to load available variants
3. **Select variants** from dropdown
4. **Selected variants appear** as badges with details
5. **Click X** to remove a variant

**Variant Badge Display:**

```
┌────────────────────────────────┐
│ 🎨 Color Name    🔢 SKU  │
│ 📏 Size/Custom Value        │
│                              │
│        [Remove Button]         │
└────────────────────────────────┘
```

---

## Creating the Product

### Review Before Submitting

!!! warning "Quality Check"
Take a moment to review all information before submitting. Errors here create problems later.

**Checklist:**

| Category       | Items to Verify                                                                                            |
| -------------- | ---------------------------------------------------------------------------------------------------------- |
| **Basic Info** | ✅ Name is clear and descriptive ✅ Provider selected ✅ Category appropriate ✅ Rating reflects quality   |
| **Pricing**    | ✅ All prices set and reasonable ✅ Margins are healthy ✅ Special pricing configured if needed            |
| **Media**      | ✅ At least one high-quality image ✅ Additional images show different angles ✅ Video included if helpful |
| **Settings**   | ✅ Variant type matches actual variations ✅ Visibility settings correct ✅ Seller access appropriate      |
| **Variants**   | ✅ Selected variants exist in inventory ✅ No duplicates or errors                                         |

### Submit the Form

!!! tip "Submission Process"
The system validates everything, creates the product, and makes it available.

**What Happens:**

1. **Validation** - System checks all information is correct
2. **Product Creation** - Product created in database
3. **Media Processing** - Images linked to product
4. **Variant Association** - Selected variants linked
5. **Price Setup** - All prices saved including special pricing
6. **Inventory Setup** - Product added to inventory system

**Success Flow:**

```
[Submit Form]
    ↓
[Validation Passes]
    ↓
[Product Created]
    ↓
[Success Message]
    ↓
[Redirect to Product List]
    ↓
[Product Visible to Sellers]
```

**Error Flow:**

```
[Submit Form]
    ↓
[Validation Fails]
    ↓
[Error Messages Displayed]
    ↓
[Form Preserved]
    ↓
[Fix and Resubmit]
```

---

## Business Best Practices

### Product Naming

!!! success "Naming Excellence"
Good product names are clear, descriptive, and professional.

**Guidelines:**

| Do                                                | Don't                               |
| ------------------------------------------------- | ----------------------------------- |
| Use **clear, descriptive names**                  | Use internal codes                  |
| Include **key product attributes**                | Use abbreviations                   |
| Keep names **consistent** across similar products | Be inconsistent                     |
| Use **standard industry terminology**             | Use jargon sellers won't understand |

**Examples:**

- ✅ **Good**: "Cotton T-Shirt - Summer Collection"
- ✅ **Good**: "Wireless Bluetooth Earbuds - Noise Canceling"
- ❌ **Bad**: "TS-2024-001"
- ❌ **Bad**: "Product A"

### Pricing Strategy

!!! tip "Pricing Science"
Strategic pricing affects margins, competitiveness, and seller relationships.

**Key Considerations:**

| Pricing Factor          | Questions to Ask                                |
| ----------------------- | ----------------------------------------------- |
| **Competitive Pricing** | What are competitors charging?                  |
| **Profit Margins**      | Does this pricing allow healthy margins?        |
| **Channel Differences** | Should POS pricing differ from online?          |
| **Volume Discounts**    | Can we offer special pricing for large sellers? |
| **Market Positioning**  | Is this a premium or value product?             |

**Margin Formula:**

```
Selling Price - Buy Price = Profit Margin

Example:
Selling Price: $50
Buy Price: $25
Profit Margin: $25 (50% margin)
```

### Media Guidelines

!!! success "Visual Quality"
Professional media builds seller confidence and increases conversions.

**Image Best Practices:**

| Practice                                                    | Why It Matters                       |
| ----------------------------------------------------------- | ------------------------------------ |
| **Use professional-quality images**                         | Professional appearance builds trust |
| **Show product from multiple angles**                       | Complete product understanding       |
| **Include scale references** (e.g., product next to a coin) | Buyers understand actual size        |
| **Use consistent lighting**                                 | Professional catalog appearance      |
| **Maintain clean backgrounds**                              | Easier integration into catalog      |
| **Show product in use**                                     | Helps buyers understand application  |

**Video Best Practices:**

| Practice                                 | Why It Matters                      |
| ---------------------------------------- | ----------------------------------- |
| **Demonstrate key features**             | Shows product capabilities          |
| **Include close-ups**                    | Shows product details               |
| **Show product in use**                  | Helps buyers understand application |
| **Keep videos short**                    | Maintains viewer engagement         |
| **Use good audio** if voiceover included | Professional quality                |

### Variant Management

!!! tip "Variant Strategy"
Only create variants that actually exist in your inventory.

**Guidelines:**

| Variant Type   | When to Use                 | Examples                               |
| -------------- | --------------------------- | -------------------------------------- |
| **None**       | Single-SKU products         | Accessories, basic items               |
| **Color/Size** | Standard product variations | T-shirts, shoes, clothing              |
| **Custom**     | Specialized variations      | Custom products, specialized equipment |

**Tips:**

- ✅ Use **Color/Size** for standard clothing variations
- ✅ Use **Custom** for specialized product types
- ✅ Keep variant names **simple and descriptive**
- ✅ **Refresh variant list** if you've created new variants

### Access Control

!!! example "Access Strategy"
Choose access control based on your product strategy and seller relationships.

**Decision Matrix:**

| Situation                                 | Best Setting                   | Why                       |
| ----------------------------------------- | ------------------------------ | ------------------------- |
| **Standard product, wide distribution**   | Public, Normal seller type     | Maximum reach             |
| **Premium product, limited availability** | Private, VIP sellers           | Exclusivity, higher value |
| **Wholesale product**                     | Public, special seller pricing | Competitive pricing       |
| **Partner-exclusive product**             | Private, specific sellers      | Partnership benefits      |

---

## Common Scenarios

### Scenario 1: Adding a New Clothing Item

!!! example "Clothing Product"
This is the most common product type in many catalogs.

**Workflow:**

1. **Basic Info**

   - Name: "Cotton T-Shirt - Summer Collection"
   - Provider: "Fashion Co."
   - Category: "Clothing"
   - Rating: "4 stars"

2. **Pricing**

   - Buy Price: $15
   - Selling Price: $35
   - Old Price: $45 (sale)
   - POS Price: $35
   - Warehouse Price: $15

3. **Media**

   - Upload 4 images (front, back, side, detail shot)
   - No video (not needed)

4. **Settings**

   - Minimum Seller Type: "Normal"
   - Variant Type: "Color/Size"
   - Public: "Yes"

5. **Variants**

   - Select: "Red-Large", "Red-Medium", "Blue-Large", "Blue-Medium"

6. **Submit**
   - Click "Create Product"

**Outcome:**

- ✅ Professional product catalog entry
- ✅ Accurate pricing across channels
- ✅ Complete variant structure
- ✅ High-quality images for sellers
- ✅ Available to all eligible sellers

### Scenario 2: Adding an Exclusive Product for VIP Sellers

!!! example "Exclusive Product"
Exclusivity creates perceived value and rewards high-performing sellers.

**Workflow:**

1. **Basic Info**

   - Name: "Luxury Watch - Gold Edition"
   - Provider: "Swiss Watchmakers"
   - Category: "Accessories"
   - Rating: "5 stars"

2. **Pricing**

   - Buy Price: $200
   - Selling Price: $500
   - No Old Price
   - POS Price: $500
   - Warehouse Price: $200

3. **Media**

   - Upload high-quality images
   - Add demonstration video showing features

4. **Settings**

   - Minimum Seller Type: "VIP"
   - Variant Type: "None"
   - Public: "No"
   - Allowed Sellers: "VIP Seller A", "VIP Seller B"

5. **Variants**

   - No variants (single SKU)

6. **Submit**
   - Click "Create Product"

**Outcome:**

- ✅ Exclusive product for VIP sellers
- ✅ Premium positioning
- ✅ High-quality media
- ✅ Seller loyalty building
- ✅ Higher perceived value

### Scenario 3: Adding a Product with Wholesale Pricing

!!! example "Wholesale Strategy"
Special pricing enables competitive bulk purchasing.

**Workflow:**

1. **Basic Info**

   - Name: "Bulk T-Shirt Pack"
   - Provider: "Textile Co."
   - Category: "Clothing"
   - Rating: "3 stars"

2. **Pricing**

   - Buy Price: $80
   - Selling Price: $120
   - Old Price: $150
   - POS Price: $120
   - Warehouse Price: $80
   - **Special Seller Pricing**: "Wholesale Seller" at $100 per pack

3. **Media**

   - Upload pack images showing contents

4. **Settings**

   - Normal seller access
   - Public
   - No variants

5. **Submit**
   - Click "Create Product"

**Outcome:**

- ✅ Standard pricing for most sellers
- ✅ Wholesale pricing for bulk buyers
- ✅ Competitive positioning
- ✅ Flexible access control

---

## Troubleshooting

### Form Won't Submit

!!! warning "Common Issues"
Most submission failures are due to missing required fields or invalid data.

| Problem                     | Solution                                         |
| --------------------------- | ------------------------------------------------ |
| **Required fields missing** | Fill all fields marked with red asterisks        |
| **No images uploaded**      | Upload at least one image (required)             |
| **Invalid prices**          | Ensure all prices are positive numbers           |
| **Variant selection error** | Check that variant selections match variant type |

### Images Won't Upload

!!! tip "Image Upload Tips"
Image upload issues are usually file-related.

| Problem            | Solution                             |
| ------------------ | ------------------------------------ |
| **File too large** | Reduce image size or compress file   |
| **Wrong format**   | Use JPG, PNG, or WEBP                |
| **Network issues** | Check internet connection and retry  |
| **Browser issues** | Try different browser or clear cache |

### Variants Not Appearing

!!! info "Variant Loading"
Variants need to exist in the system before you can select them.

| Problem                    | Solution                                   |
| -------------------------- | ------------------------------------------ |
| **No variants showing**    | Ensure variant type is selected            |
| **Variants outdated**      | Click "Refresh" button to reload           |
| **Variants don't exist**   | Create variants first, then add to product |
| **Recent variant changes** | Refresh page to see new variants           |

### Special Seller Pricing Issues

!!! tip "Special Pricing Setup"
Special pricing requires sellers to exist in the system.

| Problem              | Solution                                  |
| -------------------- | ----------------------------------------- |
| **Seller not found** | Ensure seller exists and is active        |
| **Invalid price**    | Price must be a positive number           |
| **Duplicate entry**  | Seller is already in special pricing list |
| **Price too low**    | Ensure price covers your costs            |

---

## Permissions

!!! info "Access Control"
Product creation requires specific permissions.

| Action          | Required Permission | Who Typically Has It |
| --------------- | ------------------- | -------------------- |
| Create products | `products:create`   | Admin users          |

---

## Next Steps

- 📋 After creating a product, view it in the [Product List](./product-list.md)
- ✏️ Edit product details on the [Product Edit](./product-edit.md) page
- 🏷️ Generate barcodes on the [Product Details](./product-details.md) page
