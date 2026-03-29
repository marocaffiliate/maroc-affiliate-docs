# Product Edit Page

## Overview

The Product Edit page allows you to modify existing products while protecting important business data. Think of it as maintaining your product catalog while preserving historical records.

## Purpose

This page helps you:

- Update product information as needs change
- Adjust pricing as costs or market conditions change
- Update images and descriptions
- Add or remove product variants
- Manage seller access
- Correct errors or improve product listings

## Important: Business Restrictions

Some product information is **protected** based on business rules. These restrictions prevent data corruption and preserve history.

### Why Restrictions Exist

Products are connected to critical business data:

- **Orders**: Customer purchases reference product codes and details
- **Purchases**: Supplier orders reference original prices
- **Stock Movements**: Inventory history tracks changes over time

Changing certain fields after these transactions would:

- Break order history and customer records
- Corrupt financial reporting
- Invalidate inventory tracking
- Create audit trail problems

### What Gets Locked

**Product Code**: Locked if product has customer orders

- Orders reference product codes for invoices, shipping, etc.
- Cannot be changed once orders exist
- You'll see a "Protected" badge on this field

**Variant Type**: Locked if product has customer orders

- Orders reference specific variant types (colors, sizes, etc.)
- Changing variant type breaks order mapping
- The variant dropdown becomes disabled

### What Shows Warnings

**Price Changes**: Warning if product has purchase orders

- Purchase orders use original prices for cost tracking
- Changing prices affects historical financial analysis
- You'll see a warning message, but can still edit

**Stock/Variant Changes**: Warning if product has inventory movements

- Stock movements track inventory history
- Changes affect historical inventory records
- You'll see a warning to be cautious

## Understanding to Alert Banner

When restrictions apply, you'll see a warning banner at the top:

**What It Shows**:

- **Shield icon**: Indicates business restrictions are active
- **Warning messages**: Specific explanation of what's protected
- **Action items**: What you can and cannot do

**Example Messages**:

- "Product code is locked due to existing orders"
- "Price changes will affect purchase order history"
- "Stock movements exist - be careful with variant changes"

## What You Can Edit

### 1. Basic Information (Mostly Editable)

**Product Name**: Always editable

- Update to correct typos
- Add or remove details
- Improve clarity
- Changes appear everywhere immediately

**Provider**: Always editable

- Change supplier if you switch vendors
- Update contact information
- Affects purchase history tracking

**Category**: Always editable

- Recategorize products
- Improve catalog organization
- Affects how sellers browse products

**Product Code**: Conditionally editable

- **Editable**: No orders exist yet
- **Locked**: Orders exist (shows "Protected" badge)
- If locked, you cannot change it

**Variant Type**: Conditionally editable

- **Editable**: No orders exist yet
- **Locked**: Orders exist (dropdown disabled)
- If locked, you must use existing variant type

**Rating**: Always editable

- Update based on feedback or quality assessments
- Helps sellers understand product quality

### 2. Pricing (All Editable, With Warnings)

All price fields are always editable, but you may see warnings:

**Buy Price**: Editable (warning if purchases exist)

- Update when supplier costs change
- Affects profit margins
- Warning: "Price changes will affect purchase order history"

**Selling Price**: Editable (warning if purchases exist)

- Adjust based on market conditions
- Respond to competition
- Warning: "Price changes will affect purchase order history"

**Old Price**: Always editable

- Update for sales and promotions
- Cross-out price for discount perception
- Remove when sale ends

**POS Price**: Always editable

- Adjust for in-store strategy
- Different from online pricing if needed
- Affects POS transactions only

**Warehouse Price**: Always editable

- Update for inventory valuation
- Internal pricing only
- Not visible to sellers

**Special Seller Pricing**: Fully editable

- Add new seller-specific prices
- Update existing special prices
- Remove entries by clicking X
- Edit inline by changing price numbers

### 3. Media (Fully Editable)

**Images**: Always editable

- Add new images
- Remove existing images
- Reorder images by dragging
- Replaces current image set
- Best practice: Keep images consistent

**Video**: Always editable

- Upload new video
- Replace current video
- Remove video entirely
- Video helps demonstrate complex products

### 4. Product Description (Fully Editable)

- Update with new information
- Improve clarity and completeness
- Add features or specifications
- Fix errors or typos
- Changes appear on seller pages immediately

### 5. Access Control (Fully Editable)

**Minimum Seller Type**: Always editable

- Change who can see the product
- Upgrade or downgrade access level
- Affects seller visibility immediately

**Public/Private**: Always editable

- Switch between public and private
- Change product visibility scope
- Affects seller access immediately

**Allowed Sellers**: Editable if product is private

- Add or remove specific sellers
- Update access list as relationships change
- Only visible if product is set to Private

### 6. Variant Management (Fully Editable)

Add or remove product variants:

- **Add variants**: Assign new variants to product
- **Remove variants**: Remove existing variant assignments
- **Manage stock**: Update inventory levels per variant
- **Update pricing**: Set variant-specific prices if needed
- **Generate barcodes**: Create QR codes for variants

## Editing Scenarios

### Scenario 1: Correcting a Typo in Product Name

**Status**: No orders exist yet
**What You Can Edit**:

- Product name ✓
- Product code ✓
- Variant type ✓
- Everything else ✓

**Process**:

1. Update product name with correct spelling
2. Review other information for accuracy
3. Click "Update Product"
4. Changes take effect immediately

### Scenario 2: Updating Price After Supplier Cost Change

**Status**: Product has existing purchase orders
**What You Can Edit**:

- Selling price ✓ (with warning)
- Buy price ✓ (with warning)
- Product code ✗ (locked)
- Variant type ✗ (locked)

**Process**:

1. See warning banner about purchase order history
2. Update buy price to new supplier cost
3. Adjust selling price to maintain margins
4. Consider updating old price to show original was higher
5. Click "Update Product"
6. Document price change reason internally

### Scenario 3: Adding New Variants to Existing Product

**Status**: Product has customer orders
**What You Can Edit**:

- Add new variants ✓ (of same type)
- Remove existing variants ✓
- Product code ✗ (locked)
- Change variant type ✗ (locked)

**Process**:

1. See variant type is locked (orders exist)
2. Click "Add Variant" to add new color/size combinations
3. Set pricing and stock for new variants
4. Generate barcodes for new variants
5. Click "Update Product"

### Scenario 4: Making a Private Product Public

**Status**: Product has existing orders
**What You Can Edit**:

- Public/Private toggle ✓
- Allowed sellers ✓
- Product code ✗ (locked)

**Process**:

1. Change "Private" to "Public"
2. Allowed sellers field disappears (not needed for public)
3. All eligible sellers can now see product
4. Click "Update Product"

## What Happens When You Submit

### Validation

The system checks:

- All required fields are filled
- Prices are positive numbers
- At least one image exists
- Variant selections are valid
- Business restrictions are respected

### Success

If validation passes:

- Product is updated in the database
- Changes appear immediately
- You'll see a success message
- Page reloads to show updated information

### Errors

If validation fails:

- Error messages explain what's wrong
- Form preserves your entries
- Fix issues and resubmit

## Business Best Practices

### Editing Products with Orders

**Focus on**: Description, images, pricing, adding variants of current type
**Avoid**: Changing product code or variant type
**Consider**: Impact on order history and customer communications

### Editing Products with Purchase Orders

**Focus on**: Pricing updates with care, documentation of changes
**Avoid**: Frequent price changes that confuse financial analysis
**Consider**: Creating new product variant for price changes

### Editing Products with Stock Movements

**Focus on**: Updating stock levels (via inventory management), not variant structure
**Avoid**: Removing variants that have stock history
**Consider**: Impact on inventory tracking and audit trails

### Making Visibility Changes

**When Making Public**: Communicate to all eligible sellers about new product availability
**When Making Private**: Communicate to affected sellers about product removal
**When Changing Seller Type**: Inform sellers about access changes

### Updating Media

**Best Practices**:

- Maintain consistent quality across images
- Use recent, accurate photos
- Show product features clearly
- Demonstrate usage with video if helpful
- Keep file sizes reasonable

### Pricing Updates

**When Updating**:

- Document reason for price change
- Consider competitive pricing
- Maintain profit margins
- Communicate changes to sellers if significant
- Update old price to create sale effect if appropriate

## Common Issues

### Can't Edit Product Code

**Reason**: Product has customer orders

**Solution**:

- Leave code as-is
- Product code is permanent reference for order history
- Cannot be changed due to business rules

### Variant Type Dropdown Disabled

**Reason**: Product has customer orders

**Solution**:

- Cannot change variant type
- Can add/remove variants of current type
- Create new product if different variant type needed

### See Price Change Warning

**Reason**: Product has purchase orders

**Solution**:

- Proceed with caution
- Understand that historical analysis will show old prices
- Document price change reasons
- Consult with finance team if unsure

### Form Won't Submit

**Possible Causes**:

- Missing required fields
- Invalid price values
- No images uploaded
- Invalid variant selections

**Solution**:

- Check for error messages
- Fill all required fields
- Verify prices are positive
- Ensure at least one image
- Check variant assignments

## Data Integrity

### Order History Protection

- Orders permanently reference product codes
- Changing codes would break order tracking
- Customer invoices and shipping labels would be wrong
- System prevents this by locking codes

### Financial Record Preservation

- Purchase orders reference original prices
- Historical analysis depends on stable prices
- System allows price changes but warns about impact
- Original prices are preserved in purchase order records

### Inventory Tracking Consistency

- Stock movements reference specific variants
- Changing variant structure affects tracking
- System allows adding/removing variants but warns
- Original variant assignments remain in inventory history

## Permissions

This page requires:

- **products:view**: View product details
- **products:edit**: Make changes to products

## Next Steps

- Return to [Product List](./product-list.md) to see updated products
- Create new products on the [Product Creation](./product-creation.md) page
- Generate barcodes on the [Product Details](./product-details.md) page
