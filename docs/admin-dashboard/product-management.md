# Admin Dashboard - Product Management

This section covers the product management pages in the admin dashboard. As a new developer, you'll need to understand how products are listed, created, and edited in the system.

## Overview

The product management system allows administrators to:

- View and filter all products in the platform
- Create new products with variants and pricing
- Edit existing products with business restrictions
- Manage product variants, images, and seller access

## Product List Page

### Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/page.tsx`

### Purpose

Display all products with filtering, sorting, and bulk operations.

### Key Features

#### Data Fetching

The page fetches data in parallel using:

- `getProducts()` - Paginated product list with filters
- `getProductStatusCounts()` - Count products by status (DRAFT, AVAILABLE, etc.)
- `getProductCategoryCounts()` - Count products by category
- `getProductVariantTypeCounts()` - Count products by variant type

#### Filtering Options

Products can be filtered by:

- **Search** - Searches across name, code, and description
- **Name** - Exact name contains
- **Code** - Product code contains
- **Status** - Product status (DRAFT, AVAILABLE, OUT_OF_STOCK, etc.)
- **Category** - Product category
- **Variant Type** - NONE, COLOR_SIZE, CUSTOM
- **Minimum Seller Type** - NORMAL, PRO, VIP
- **Public/Private** - Whether product is public
- **Date Range** - Creation date range

#### Data Table

Uses `DataTable` component with:

- Column sorting (default: updatedAt descending)
- Row selection for bulk operations
- Action buttons per row
- Pagination

#### Columns

- Product image
- Product name and code
- Category
- Status
- Variant type
- Variants count
- Stock indicators
- Pricing (selling price, POS price)
- Actions (edit, delete)

#### Bulk Operations

- Delete multiple selected products
- Requires `products:delete` permission

### Permissions

- `products:view` - Required to view product list
- `products:create` - Required to see "Create Product" button
- `products:delete` - Required for delete operations

### Technical Implementation

```typescript
// Server component handles data fetching
const [data, statusCounts, categoryCounts, variantTypeCounts] = await Promise.all([
  getProducts(search),
  getProductStatusCounts(),
  getProductCategoryCounts(),
  getProductVariantTypeCounts()
])

// Client component renders table with filtering
<ProductsTable promises={promises} dictionary={dictionary} />
```

### Query Implementation

The `getProducts` function in `_lib/queries.ts`:

- Validates search parameters with Zod schema
- Builds Prisma where clause from filters
- Supports array filters (comma-separated or array)
- Handles date ranges with timezone-aware parsing
- Implements sorting by multiple columns
- Returns paginated data with metadata

### Caching

Products data is cached with:

- 1-minute revalidation for product list
- 60-second revalidation for status counts
- 5-minute revalidation for category/variant type counts
- Cache tags for invalidation: `["products", "product-status-counts"]`

## Product Creation Page

### Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/page.tsx`

### Purpose

Create new products with all required information.

### Form Sections

#### 1. Basic Information

- **Name** - Product name (required)
- **Provider** - Select from available providers
- **Category** - Select from product categories
- **Rating** - 0-5 stars rating
- **Description** - Rich text editor for detailed description

#### 2. Pricing

- **Buy Price** - Cost to acquire the product
- **Selling Price** - Standard selling price
- **Old Price** - Original price (for discounts)
- **POS Price** - Point of Sale price
- **Warehouse Price** - Internal warehouse price
- **Special Seller Pricing** - Custom prices for specific sellers

#### 3. Media

- **Images** - Upload multiple product images via UploadThing
- **Video** - Upload product video (optional)

#### 4. Settings

- **Minimum Seller Type** - NORMAL, PRO, VIP (who can see the product)
- **Variant Type** - NONE, COLOR_SIZE, CUSTOM
- **Public/Private** - Whether product is visible to all sellers
- **Allowed Sellers** - Select specific sellers if not public

#### 5. Product Variants

Select existing variants to associate with the product:

- Refresh button to reload variants
- Filter by variant type
- Color swatches for color variants
- Display variant SKU and description
- Selected variants shown as badges

### Form Validation

Uses Zod schema `createProductSchemaRefined` with:

- Required fields validation
- Price positivity checks
- SKU uniqueness
- At least one image required
- Valid variant selections

### Auto-generated Fields

- **Product Code** - Auto-generated from name: `{NAME}-{TIMESTAMP}`
- Example: `T-SHIRT-ABC123456`

### Variant Management

When creating products:

1. Select variant type (NONE, COLOR_SIZE, CUSTOM)
2. Fetch available variants for that type
3. Select multiple variants to assign
4. Variants can be created separately via standalone variant creator

### Special Features

- Form uses `useTransition` for optimistic UI updates
- Auto-generated product codes from name
- Real-time variant filtering by type
- Multi-select for sellers and variants
- Rich text editor for descriptions
- Drag-and-drop image uploads

### Permissions

- `products:create` - Required to access create page

### Technical Implementation

```typescript
// Server component fetches form options
const [dictionary, options] = await Promise.all([
  getDictionary(locale),
  getProductFormOptions(),
]);

// Client component handles form state
export function CreateProductPageContent({ options, dictionary, locale }) {
  const methods = useForm<CreateProductInput>({
    resolver: zodResolver(createProductSchemaRefined),
    defaultValues: {
      /* ... */
    },
  });

  // Form submission with transition
  const onSubmit = async (data: CreateProductInput) => {
    startTransition(async () => {
      const result = await createProductAction(data);
      if (result.success) {
        router.push("/dashboards/admin/products");
      }
    });
  };
}
```

### Form Options

The page fetches options via `getProductFormOptions()`:

- `providers` - Available product providers
- `categories` - Product categories
- `sellers` - Active sellers in the system
- `productVariants` - Available variants for products

## Product Edit Page

### Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/page.tsx`

### Purpose

Edit existing products with business logic restrictions.

### Business Restrictions

The edit page enforces business rules to prevent data corruption:

#### Code Locking

- **When Locked**: Product has orders
- **Reason**: Order history references product codes
- **Impact**: Product code becomes read-only

#### Price Changes

- **When Warning**: Product has purchases
- **Reason**: Purchase orders use original prices
- **Impact**: Warning displayed but still editable

#### Variant Type Changes

- **When Locked**: Product has orders
- **Reason**: Orders reference specific variant types
- **Impact**: Variant type dropdown disabled

#### Stock Movement Protection

- **When Warning**: Product has stock movements
- **Reason**: Stock history tracked per variant
- **Impact**: Warning displayed about data integrity

### Restriction Alerts

When restrictions apply, an alert banner shows:

```typescript
{
  canChangeCode: !hasOrders,
  canChangePrices: true,
  hasBusinessRelations: hasOrders || hasPurchases || hasStockMovements
}
```

### Form Sections (Same as Creation)

The edit page has the same sections as creation, with:

- Pre-populated fields from existing product
- Disabled fields based on restrictions
- Additional validation based on business state

### Key Differences from Creation

#### Read-only Fields

- Product code (if product has orders)
- Variant type (if product has orders)

#### Additional Features

- Restriction alerts at the top
- Protected field badges
- Business rule validation
- Warning messages for critical operations

#### Variant Management

- **Inline variant editing**: Modify variant assignments
- **Stock management**: Adjust stock levels per variant
- **Pricing updates**: Update variant-specific pricing
- **Barcode generation**: Generate/print barcodes per variant

### Form Validation

Uses `createEditProductSchemaWithContext` with:

- Context-aware validation (original product state)
- Business rule enforcement
- Field restrictions based on business state
- Prevents invalid state transitions

### Permissions

- `products:edit` - Required to edit products
- `products:view` - Required to view product details

### Technical Implementation

```typescript
// Server component fetches product and options
const [dictionary, product, options] = await Promise.all([
  getDictionary(locale),
  getProductForEdit(productId),
  getProductFormOptions(),
]);

if (!product) {
  notFound();
}

// Check business restrictions
const hasOrders = product.productVariantAssignments.some(
  (assignment) => assignment._count.orderItems > 0,
);

// Client component with restriction awareness
const methods = useForm<FormData>({
  resolver: zodResolver(
    createEditProductSchemaWithContext({
      originalProduct: product,
      hasOrders,
      hasPurchases,
      hasStockMovements,
      canChangeCode: !hasOrders,
      canChangeVariantType: !hasOrders,
    }),
  ),
});
```

### Page Flow

1. Fetch product data with relations
2. Check business restrictions (orders, purchases, stock movements)
3. Initialize form with product data
4. Display restrictions alert if applicable
5. Render form with disabled fields based on restrictions
6. Submit changes with validation
7. Refresh page on success

## Common Patterns

### 1. Data Fetching Pattern

```typescript
// Parallel data fetching
const [data, counts, options] = await Promise.all([
  getProducts(filters),
  getProductCounts(),
  getFormOptions(),
]);
```

### 2. Permission Gates

```typescript
// UI-level permission check
<PermissionGate permission="products:create">
  <Button>Create Product</Button>
</PermissionGate>

// Server-side permission check
await requirePermission("products:view")
```

### 3. Form State Management

```typescript
// React Hook Form with Zod validation
const methods = useForm<FormData>({
  resolver: zodResolver(schema),
  defaultValues: initialValues,
});

// Transition for optimistic updates
const [isPending, startTransition] = useTransition();
```

### 4. Error Handling

```typescript
// Action result handling
const result = await createProductAction(data);
if (result.success) {
  toast.success(result.message);
  router.push("/products");
} else {
  toast.error(result.error);
}
```

### 5. Variant Loading Pattern

```typescript
// Watch variant type changes
const variantType = methods.watch("variantType");

// Fetch variants when type changes
useEffect(() => {
  async function fetchVariantsByType() {
    if (!variantType) return;
    setLoadingVariants(true);
    try {
      const result = await getProductVariantsByType(variantType);
      setFilteredVariants(result.productVariants);
    } finally {
      setLoadingVariants(false);
    }
  }
  fetchVariantsByType();
}, [variantType]);
```

## Related Files

### Page Routes

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/page.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/new/page.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/edit/page.tsx`

### Components

- `products/_components/products-table.tsx`
- `products/_components/products-table-columns.tsx`
- `products/new/_components/product-create-form.tsx`
- `products/new/_components/create-product-page-content.tsx`
- `products/[id]/edit/_components/edit-product-form.tsx`
- `products/[id]/edit/_components/edit-product-page-content.tsx`

### Server Actions

- `products/_lib/actions.ts` - createProductAction, updateProductAction
- `products/_lib/queries.ts` - getProducts, getProductStatusCounts, etc.
- `products/_lib/validations.ts` - Zod schemas

### Types

- `products/types.ts` - ProductWithRelations, ProductFormOptions

## Next Steps

Now that you understand the product management pages:

1. Study the server actions to understand data mutations
2. Review the variant system in detail
3. Understand the permission system
4. Explore the seller dashboard to see how products are consumed
