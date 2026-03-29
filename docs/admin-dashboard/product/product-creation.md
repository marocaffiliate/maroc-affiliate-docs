# Product Creation Page

## Overview

The Product Creation page allows administrators to add new products to the marocAffiliate platform with all required information, pricing, variants, and media.

## Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/page.tsx`

## Purpose

Create new products with complete information including basic details, pricing, media, settings, and variant assignments.

## Page Structure

### Form Sections

#### 1. Basic Information Card

Contains essential product details:

- **Name**: Product name (required, auto-generates code)
- **Provider**: Select from available providers
- **Category**: Product category classification
- **Rating**: 0-5 stars rating system
- **Description**: Rich text editor for detailed product description

##### Auto-Generated Code

When product name is entered, a unique product code is automatically generated:

```typescript
Format: {
  NAME;
}
-{ TIMESTAMP };
Example: T - SHIRT - ABC123456;
```

#### 2. Pricing Card

Contains all price fields:

- **Buy Price**: Cost to acquire product (required)
- **Selling Price**: Standard selling price for customers (required)
- **Old Price**: Original price (for discounts/marketing)
- **POS Price**: Point of Sale price for in-store sales
- **Warehouse Price**: Internal warehouse price
- **Special Seller Pricing**: Custom prices for specific sellers

##### Special Seller Pricing

Assign custom prices to specific sellers:

- Select seller from dropdown
- Enter custom price
- Click "Add" to add to list
- Remove entries with X button
- Multiple special prices supported

#### 3. Media Card

Upload product images and videos:

- **Images**: Multiple product images via UploadThing
- **Video**: Product video (optional, max one)

##### Image Upload

- Drag and drop support
- Multiple images allowed
- Image preview thumbnails
- Remove individual images
- Reorder images (drag to reorder)

##### Video Upload

- Single video upload
- Video preview player
- Video validation (size, format)

#### 4. Settings Card

Product visibility and access control:

- **Minimum Seller Type**: Who can see the product (NORMAL/PRO/VIP)
- **Variant Type**: Product variant system (NONE/COLOR_SIZE/CUSTOM)
- **Public/Private**: Visibility to sellers
- **Allowed Sellers**: Select specific sellers if not public

##### Visibility Logic

```typescript
if (isPublic) {
  // Product visible to all sellers meeting minimum type
} else {
  // Product visible only to selected sellers
}
```

#### 5. Product Variants Card

Associate existing variants with the product:

- Select variant type (NONE/COLOR_SIZE/CUSTOM)
- Fetch available variants for selected type
- Select multiple variants to assign
- Refresh button to reload variants
- Color swatches for visual variant selection

##### Variant Selection Flow

1. Select variant type from dropdown
2. Variants load automatically based on type
3. Use multi-select to choose variants
4. Selected variants shown as badges with details
5. Clear all with "Clear All" button

##### Variant Display

Each selected variant badge shows:

- Variant name
- SKU code
- Description (color/size or custom type/value)
- Color swatch (if applicable)
- Remove button

## Form Validation

### Zod Schema

Uses `createProductSchemaRefined` with comprehensive validation:

#### Required Fields

```typescript
{
  name: string,              // Product name (min length: 3)
  code: string,              // Auto-generated, must be unique
  categoryId: number,         // Category must be selected
  providerId: string,        // Provider must be selected
  buyPrice: number,          // Must be positive
  sellingPrice: number,      // Must be positive
  images: array,            // At least one image required
  variantType: enum,        // Valid variant type
  minimumSellerType: enum    // Valid seller type
}
```

#### Price Validation

- All prices must be positive numbers
- Selling price should be greater than buy price
- POS and warehouse prices can be zero
- Special seller prices must be positive

#### Variant Validation

- If variantType is NONE, no variants selected
- If variantType is COLOR_SIZE, at least one variant required
- If variantType is CUSTOM, at least one variant required
- Variant must exist in database

#### Media Validation

- At least one image required
- Maximum file size limits
- Supported formats: JPG, PNG, GIF, WEBP
- Video: MP4, WEBM (max 100MB)

## Form State Management

### React Hook Form

Uses React Hook Form with Zod resolver:

```typescript
const methods = useForm<CreateProductInput>({
  resolver: zodResolver(createProductSchemaRefined),
  defaultValues: {
    name: "",
    code: "",
    providerId: "",
    categoryId: 0,
    buyPrice: 0,
    sellingPrice: 0,
    posPrice: 0,
    wareHousePrice: 0,
    images: [],
    video: [],
    description: "",
    ratingStars: 0,
    minimumSellerType: SellerType.NORMAL,
    variantType: VariantType.COLOR_SIZE,
    isPublic: true,
    allowedSellerIds: [],
    productVariantIds: [],
    specialSellerPricing: [],
  },
});
```

### State Sync

Form state synced with UI components:

```typescript
// Auto-generate code from name
useEffect(() => {
  const subscription = methods.watch((value, { name }) => {
    if (name === "name" && value.name) {
      const generatedCode = `${value.name
        .toUpperCase()
        .replace(/[^A-Z0-9]/g, "")
        .slice(0, 10)}-${Date.now().toString().slice(-6)}`;
      methods.setValue("code", generatedCode);
    }
  });
  return () => subscription.unsubscribe();
}, [methods]);

// Sync variant selections
useEffect(() => {
  methods.setValue("productVariantIds", selectedVariants, {
    shouldValidate: true,
  });
}, [selectedVariants, methods]);
```

## Variant Management

### Fetching Variants

Variants are fetched based on selected type:

```typescript
const variantType = methods.watch("variantType");

useEffect(() => {
  async function fetchVariantsByType() {
    if (!variantType) return;
    setLoadingVariants(true);
    setSelectedVariants([]); // Clear selections when type changes

    try {
      const result = await getProductVariantsByType(variantType);
      if (result.success && result.productVariants) {
        setFilteredVariants(result.productVariants);
      }
    } finally {
      setLoadingVariants(false);
    }
  }
  fetchVariantsByType();
}, [variantType]);
```

### Variant Types

#### NONE

- No variants
- Single SKU product
- No variant selection required

#### COLOR_SIZE

- Color and size combinations
- Each variant has color and size
- Color swatches for visual selection
- Example: "Red - Large"

#### CUSTOM

- Custom variant types
- Flexible variant system
- Custom type and value pairs
- Example: "Material: Cotton"

## Submission Process

### Form Submission

Uses React transitions for optimistic updates:

```typescript
const onSubmit = async (data: CreateProductInput) => {
  // Validate form
  const validationResult = createProductSchemaRefined.safeParse(data);
  if (!validationResult.success) {
    toast.error("Validation failed");
    return;
  }

  startTransition(async () => {
    try {
      const result = await createProductAction(data);
      if (result.success) {
        toast.success("Product created successfully");
        router.push("/dashboards/admin/products");
      } else {
        toast.error(result.error);
      }
    } catch (error) {
      toast.error("Something went wrong");
    }
  });
};
```

### Server Action

The `createProductAction` handles:

- Transaction management
- Product creation
- Variant assignments
- Price mappings
- Image/video processing
- Database relationships

### Success Flow

1. Form validation passes
2. Server action executes
3. Product created in database
4. Variants assigned
5. Images uploaded and linked
6. Success toast displayed
7. Redirect to product list

### Error Handling

- Validation errors show inline
- Server errors show toast messages
- Form state preserved on error
- User can retry submission

## Form Options

### Data Fetching

Page fetches form options on load:

```typescript
const [dictionary, options] = await Promise.all([
  getDictionary(locale),
  getProductFormOptions(),
]);
```

### Available Options

```typescript
{
  providers: User[],           // Available product providers
  categories: Category[],       // Product categories
  sellers: User[],             // Active sellers
  productVariants: ProductVariant[]  // Available variants
}
```

## Permissions

### Required Permissions

- `products:create` - Access create page and submit form

### Permission Gate

```typescript
<PermissionGate permission="products:create">
  <Link href="/dashboards/admin/products/new">
    <Button>Create Product</Button>
  </Link>
</PermissionGate>
```

## Technical Implementation

### Component Hierarchy

```
CreateProductPage (Server)
  └── CreateProductPageContent (Client)
      ├── ProductCreateForm
      └── StandaloneVariantCreator
```

### Key Components

#### ProductCreateForm

Main form component with all fields:

- Form state management
- Validation
- Submission handling
- Error handling

#### StandaloneVariantCreator

Separate variant creation component:

- Create new variants on-the-fly
- Refresh variant list after creation
- Independent from main form

#### UploadComponent

File upload component using UploadThing:

- Drag and drop
- File preview
- Progress indicators
- Error handling

#### RichTextEditor

WYSIWYG editor for product descriptions:

- Text formatting
- Lists
- Links
- Images

## Best Practices

### Product Naming

- Use clear, descriptive names
- Auto-generated codes based on name
- Keep names concise for code readability

### Pricing Strategy

- Set buy price first
- Selling price should include margin
- Old price for discount perception
- POS price for in-store sales
- Warehouse price for internal tracking

### Variant Management

- Use COLOR_SIZE for clothing/accessories
- Use CUSTOM for specialized products
- Use NONE for single-SKU products
- Refresh variants list if new variants added

### Media Guidelines

- Use high-quality images
- Multiple angles for products
- Consistent image dimensions
- Compress images for faster loading
- Video for complex products

### Access Control

- Use PUBLIC for general products
- Use PRIVATE with selected sellers for exclusive products
- Set appropriate minimum seller type
- Consider seller relationships

## Common Issues

### Validation Failures

- Check required fields are filled
- Ensure prices are positive numbers
- Verify at least one image is uploaded
- Check variant selections match variant type

### Variant Loading Issues

- Click refresh button
- Check variant type is selected
- Ensure variants exist in database
- Network connection issues

### Image Upload Problems

- Check file size limits
- Verify file format is supported
- Check internet connection
- Try individual file upload

### Code Generation

- Codes auto-generate from name
- Timestamp ensures uniqueness
- Don't manually modify codes
- Duplicate codes will fail validation

## Related Files

### Page Components

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/page.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_components/create-product-page-content.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_components/product-create-form.tsx`

### Server Actions

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_lib/actions.ts`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_lib/queries.ts`

### Validation

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_lib/validations.ts`

### Shared Components

- `src/components/rich-text-editor`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_components/upload.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/_components/standalone-variant-creator.tsx`

## Next Steps

- Learn about [Product List](./product-list.md)
- Learn about [Product Edit](./product-edit.md)
- Learn about [Product Details & Barcodes](./product-details.md)
