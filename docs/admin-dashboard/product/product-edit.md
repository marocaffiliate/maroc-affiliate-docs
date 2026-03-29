# Product Edit Page

## Overview

The Product Edit page allows administrators to modify existing products while enforcing business rules to prevent data corruption and maintain system integrity.

## Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/page.tsx`

## Purpose

Edit product information with business restrictions based on product's usage history (orders, purchases, stock movements).

## Business Restrictions

### Why Restrictions Matter

Products are linked to critical business data:

- **Orders**: Customer purchases reference product codes and variants
- **Purchases**: Supplier orders reference original prices
- **Stock Movements**: Inventory history tracks quantities per variant

Changing certain fields after business transactions would:

- Break order history
- Corrupt financial records
- Invalidate inventory tracking
- Create audit trail issues

### Restriction Categories

#### Code Locking

**When Locked**: Product has customer orders

**Reason**: Order history contains product codes for:

- Order confirmations
- Invoices
- Shipping labels
- Customer communications

**Impact**:

- Product code field becomes read-only
- Shows "Protected" badge
- Displays warning about business relations

**Technical Check**:

```typescript
const hasOrders = product.productVariantAssignments.some(
  (assignment) => assignment._count.orderItems > 0,
);
const canChangeCode = !hasOrders;
```

#### Variant Type Locking

**When Locked**: Product has customer orders

**Reason**: Orders reference specific variant types:

- COLOR_SIZE orders reference colors/sizes
- CUSTOM orders reference custom variants
- Changing variant type breaks order mapping

**Impact**:

- Variant type dropdown becomes disabled
- Cannot add new variant types
- Existing variant assignments remain

**Technical Check**:

```typescript
const hasOrders = product.productVariantAssignments.some(
  (assignment) => assignment._count.orderItems > 0,
);
const canChangeVariantType = !hasOrders;
```

#### Price Change Warnings

**When Warning**: Product has purchase orders

**Reason**: Purchase orders use original prices for:

- Supplier invoices
- Cost tracking
- Profit calculations
- Financial reporting

**Impact**:

- Prices remain editable
- Warning message displayed
- Users advised to be careful
- Historical prices preserved in records

**Technical Check**:

```typescript
const hasPurchases = product.productVariantAssignments.some(
  (assignment) => assignment._count.purchases > 0,
);
```

#### Stock Movement Warnings

**When Warning**: Product has inventory movements

**Reason**: Stock movements track:

- Transfer history
- Adjustment records
- Physical counts
- Discrepancy reports

**Impact**:

- Variant assignments remain editable
- Warning about data integrity
- Advised to be cautious
- History preserved

**Technical Check**:

```typescript
const hasStockMovements = product.productVariantAssignments.some(
  (assignment) => assignment._count.stockMovements > 0,
);
```

## Restriction Alert System

### Alert Banner

When any restrictions apply, an alert banner appears at the top:

```typescript
{
  canChangeCode: !hasOrders,
  canChangePrices: true,
  hasBusinessRelations: hasOrders || hasPurchases || hasStockMovements
}
```

### Alert Messages

Banner shows specific restriction messages:

```typescript
const restrictionMessages = [
  !restrictions.canChangeCode
    ? "Product code is locked due to existing orders"
    : undefined,
  hasPurchases ? "Price changes will affect purchase order history" : undefined,
  hasStockMovements
    ? "Stock movements exist - be careful with variant changes"
    : undefined,
].filter(Boolean);
```

### Visual Indicators

- **Shield icon** indicates business restrictions
- **Amber/yellow alert** for warnings
- **Protected badges** on locked fields
- **Description text** explaining restrictions

## Form Sections

### 1. Basic Information Card

Same fields as creation, with restrictions:

#### Product Name

- Always editable
- No restrictions
- Updates across all records

#### Provider

- Always editable
- Changes supplier relationship
- Updates purchase history

#### Category

- Always editable
- Affects product classification
- Updates category counts

#### Product Code

**Conditionally editable**:

- **Editable**: No orders exist
- **Locked**: Orders exist
- Shows "Protected" badge when locked
- Display lock icon

#### Variant Type

**Conditionally editable**:

- **Editable**: No orders exist
- **Locked**: Orders exist
- Dropdown disabled when locked
- Affects variant assignments

#### Rating

- Always editable
- 0-5 star scale
- Updates product quality metrics

### 2. Pricing Card

All pricing fields with warnings:

#### Buy Price

- Always editable
- Warning if purchases exist
- Updates cost basis

#### Selling Price

- Always editable
- Warning if purchases exist
- Affects customer pricing

#### Old Price

- Always editable
- For discount marketing
- Optional field

#### POS Price

- Always editable
- For in-store sales
- Affects POS transactions

#### Warehouse Price

- Always editable
- For internal tracking
- Affects inventory valuation

#### Special Seller Pricing

- Fully editable
- Add/remove seller prices
- Update existing prices
- Edit inline in list

### 3. Media Upload Card

Product images and videos:

#### Images

- Always editable
- Add/remove images
- Reorder images
- Replaces existing images

#### Video

- Always editable
- Upload new video
- Replace existing video
- Remove video

### 4. Product Description Card

Rich text editor:

- Always editable
- Full text formatting
- Updates product pages
- Affects SEO

### 5. Access Control Card

Visibility settings:

#### Minimum Seller Type

- Always editable
- Changes product visibility
- Updates seller access
- May affect sales

#### Public/Private

- Always editable
- Changes visibility scope
- Updates seller access
- Affects who can see product

#### Allowed Sellers

- Editable if product is private
- Multi-select sellers
- Updates access list
- Affects seller relationships

### 6. Variant Management Section

Manage product variants:

- **Variant Management**: Add/remove variant assignments
- **Stock Management**: Adjust stock levels per variant
- **Pricing**: Update variant-specific pricing
- **Barcodes**: Generate/print barcodes per variant

## Form Validation

### Context-Aware Validation

Uses `createEditProductSchemaWithContext` with original product state:

```typescript
const schema = createEditProductSchemaWithContext({
  originalProduct: product,
  hasOrders,
  hasPurchases,
  hasStockMovements,
  canChangeCode: !hasOrders,
  canChangeVariantType: !hasOrders,
});
```

### Validation Rules

#### Code Validation

- **Editable**: Must be unique if changed
- **Locked**: Cannot be changed
- Format: 10-20 characters
- Contains product name and timestamp

#### Variant Type Validation

- **Editable**: Must be valid variant type
- **Locked**: Cannot be changed
- Affects available variants

#### Price Validation

- Must be positive numbers
- No upper limit
- Warns about purchase history

#### Media Validation

- At least one image required
- Video optional
- Size and format restrictions

## Form State Management

### Default Values

Form pre-populated with existing product data:

```typescript
const methods = useForm<FormData>({
  resolver: zodResolver(createEditProductSchemaWithContext({...})),
  defaultValues: {
    id: product.id,
    name: product.name,
    code: product.code,
    providerId: product.providerId,
    categoryId: product.categoryId,
    buyPrice: product.buyPrice,
    sellingPrice: product.sellingPrice,
    oldPrice: product.oldPrice,
    posPrice: product.posPrice,
    wareHousePrice: product.wareHousePrice,
    images: product.images.map((url, index) => ({
      url,
      name: `image-${index}`,
      key: `key-${index}`
    })),
    video: product.video ? [{ url: product.video, name: "video", key: "video-key" }] : [],
    description: product.description || "",
    variantType: product.variantType,
    minimumSellerType: product.minimumSellerType,
    ratingStars: product.ratingStars,
    isPublic: product.isPublic,
    allowedSellerIds: product.allowedSellerIds,
    specialSellerPricing: product.specialSellerPrices.map((price) => ({
      sellerId: price.sellerId,
      price: price.price
    }))
  }
})
```

### Disabled Fields

Fields disabled based on restrictions:

```typescript
<FormControl>
  <Input
    {...field}
    placeholder={editDict.basicInfo.codePlaceholder}
    disabled={!restrictions.canChangeCode}
  />
</FormControl>
```

## Submission Process

### Update Action

```typescript
const onSubmit = (data: FormData) => {
  startTransition(async () => {
    try {
      const formattedData: EditProductInput = {
        id: data.id,
        name: data.name,
        code: data.code,
        providerId: data.providerId,
        categoryId: data.categoryId,
        buyPrice: data.buyPrice,
        sellingPrice: data.sellingPrice,
        oldPrice: data.oldPrice,
        posPrice: data.posPrice,
        wareHousePrice: data.wareHousePrice,
        images: data.images,
        video: data.video,
        description: data.description,
        ratingStars: data.ratingStars,
        variantType: data.variantType,
        minimumSellerType: data.minimumSellerType,
        isPublic: data.isPublic,
        allowedSellerIds: data.allowedSellerIds,
        specialSellerPricing: data.specialSellerPricing,
      };

      const result = await updateProductAction(formattedData);

      if (result.success) {
        toast.success(result.message);
        window.location.reload();
      } else {
        toast.error(result.error);
      }
    } catch (error) {
      toast.error("Unexpected error");
    }
  });
};
```

### Success Flow

1. Form validation passes
2. Business rules enforced
3. Product updated in database
4. Changes reflected immediately
5. Success toast displayed
6. Page reloaded to show updates

### Error Handling

- Validation errors show inline
- Business rule violations prevented
- Server errors show toast messages
- Form state preserved
- User can retry

## Permissions

### Required Permissions

- `products:view` - View product details
- `products:edit` - Edit product information

## Technical Implementation

### Component Hierarchy

```
EditProductPage (Server)
  └── EditProductPageContent (Client)
      ├── EditProductForm
      └── VariantManagementPanel
          ├── VariantManagementSection
          └── other variant components
```

### Key Components

#### EditProductForm

Main form component:

- Business restriction logic
- Protected field handling
- Context-aware validation
- Update submission

#### VariantManagementPanel

Variant management:

- Add/remove variant assignments
- Update stock levels
- Variant pricing
- Barcode generation

## Best Practices

### Editing Products with Orders

- **Code**: Cannot be changed (protected)
- **Variant Type**: Cannot be changed (protected)
- **Pricing**: Editable but be careful
- **Description**: Can be updated freely
- **Images**: Can be updated freely
- **Variants**: Edit existing, add new if type matches

### Editing Products with Purchases

- **Pricing**: Editable but affects purchase history
- **Consider**: Creating new variant for price changes
- **Document**: Price change reasons
- **Communicate**: Inform purchasing team

### Editing Products with Stock Movements

- **Variants**: Edit carefully
- **Stock**: Update via inventory management, not here
- **Barcodes**: Regenerate if needed
- **Consider**: Impact on current stock

### Making Products Public/Private

- **To Private**: Select specific sellers to grant access
- **To Public**: All eligible sellers can see product
- **Minimum Type**: Set appropriate seller type threshold
- **Consider**: Seller relationships and agreements

### Updating Media

- **Images**: Upload new ones, old ones replaced
- **Video**: Replace with new upload
- **Quality**: Maintain consistent quality
- **SEO**: Update alt text and descriptions

## Common Issues

### Cannot Edit Product Code

**Reason**: Product has customer orders

**Solution**:

- Leave code as-is
- Product code is reference for order history
- Cannot be changed due to business rules

### Variant Type Dropdown Disabled

**Reason**: Product has customer orders

**Solution**:

- Cannot change variant type
- Add variants of current type
- Create new product if different type needed

### Price Change Warnings

**Reason**: Product has purchase orders

**Solution**:

- Proceed with caution
- Document price changes
- Consider impact on financial reporting
- May need to update purchase contracts

### Validation Errors

**Common causes**:

- Missing required fields
- Invalid price values
- No images uploaded
- Invalid variant selections

**Solution**:

- Check all required fields
- Verify prices are positive
- Ensure at least one image
- Check variant assignments match type

## Data Integrity Considerations

### Order History

- Order records reference product codes
- Changing codes breaks order tracking
- Codes are permanent for ordered products

### Financial Records

- Purchase orders reference prices
- Price changes affect historical analysis
- Original prices preserved in records

### Inventory Tracking

- Stock movements reference variants
- Changing variants affects tracking
- Maintain consistent variant structure

### Audit Trail

- All changes are logged
- User who made changes recorded
- Timestamp of changes preserved
- Reasons can be documented

## Related Files

### Page Components

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/page.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_components/edit-product-page-content.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_components/edit-product-form.tsx`

### Variant Management

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_components/variant-management-panel.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_components/variant-management-section.tsx`

### Server Actions

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_lib/actions.ts`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_lib/queries.ts`

### Validation

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/_lib/validations.ts`

## Next Steps

- Learn about [Product List](./product-list.md)
- Learn about [Product Creation](./product-creation.md)
- Learn about [Product Details & Barcodes](./product-details.md)
