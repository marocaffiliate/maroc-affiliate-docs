# Product List Page

## Overview

The Product List page is the main dashboard for administrators to view, search, filter, and manage all products in the marocAffiliate platform.

## Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/page.tsx`

## Purpose

Provide a comprehensive view of the entire product catalog with advanced filtering and bulk operations.

## Key Features

### Data Display

- **Paginated table** with customizable rows per page
- **Real-time data** with 1-minute cache refresh
- **Visual indicators** for product status, stock levels, and variants
- **Sorting capabilities** across all columns

### Filtering System

Products can be filtered by multiple criteria:

#### Text Filters

- **Search**: Searches across name, code, and description (case-insensitive)
- **Name**: Exact match on product name
- **Code**: Exact match on product code

#### Select Filters

- **Status**: Product availability status (DRAFT, AVAILABLE, OUT_OF_STOCK, etc.)
- **Category**: Filter by product category
- **Variant Type**: NONE, COLOR_SIZE, CUSTOM
- **Minimum Seller Type**: NORMAL, PRO, VIP
- **Public/Private**: Show only public or private products

#### Date Range Filter

- Filter by creation date with start and end date pickers
- Date range inclusive of full day (00:00:00 to 23:59:59)

### Data Table Features

#### Columns

1. **Image**: Product thumbnail (first image)
2. **Name & Code**: Product name with code below
3. **Category**: Product category badge
4. **Status**: Current availability status
5. **Variant Type**: Type of product variants
6. **Variants Count**: Number of variant assignments
7. **Stock Indicators**: Visual stock level badges
8. **Selling Price**: Standard selling price
9. **POS Price**: Point of Sale price
10. **Actions**: Edit and delete buttons

#### Row Selection

- Click checkbox to select individual products
- "Select All" to select all visible products
- Selection persists across page changes
- Bulk delete operation on selected products

#### Sorting

- Default sort: Updated date descending (newest first)
- Click column headers to sort ascending/descending
- Multi-column sorting supported
- Sort indicators show current sort order

### Data Fetching

#### Parallel Queries

The page fetches multiple data sources in parallel:

```typescript
const promises = Promise.all([
  getProducts(search), // Paginated product list
  getProductStatusCounts(), // Products by status
  getProductCategoryCounts(), // Products by category
  getProductVariantTypeCounts(), // Products by variant type
]);
```

#### Cache Strategy

- **Product list**: 1-minute revalidation
- **Status counts**: 60-second cache
- **Category counts**: 5-minute cache
- **Variant type counts**: 5-minute cache
- **Cache tags**: `["products", "product-status-counts"]`

### Search Parameters

#### Zod Schema Validation

All search parameters are validated using `getProductsSchema`:

```typescript
{
  page: number,           // Current page (default: 1)
  perPage: number,        // Items per page (default: 10)
  search: string,         // Global search term
  name: string,           // Product name filter
  code: string,           // Product code filter
  status: string[],       // Status filter (array)
  category: string[],     // Category filter (array)
  variantType: string[],   // Variant type filter (array)
  minimumSellerType: string[], // Seller type filter (array)
  isPublic: string[],     // Public/Private filter (array)
  createdAt: number[],     // Date range filter
  sort: string[]          // Sort columns (array)
}
```

#### Array Filters

Multiple selection filters support both formats:

- URL format: `?status=DRAFT,AVAILABLE`
- Array format: `?status[]=DRAFT&status[]=AVAILABLE`

### Technical Implementation

#### Prisma Query Building

The `getProducts` function builds complex where clauses:

```typescript
// Combine all filters
if (filters.length > 0) {
  where.AND = filters;
}

// Handle date ranges
if (input.createdAt && input.createdAt.length > 0) {
  const dateFilter: any = {};
  if (input.createdAt[0]) {
    dateFilter.gte = new Date(input.createdAt[0]);
  }
  if (input.createdAt[1]) {
    dateFilter.lte = new Date(input.createdAt[1]);
  }
  filters.push({ createdAt: dateFilter });
}
```

#### Sort Handling

Special handling for nested sorting:

```typescript
if (id === "category") {
  orderBy.push({ category: { name: desc ? "desc" : "asc" } });
} else {
  orderBy.push({ [id]: desc ? "desc" : "asc" });
}
```

### Bulk Operations

#### Delete Products

- Select multiple products using checkboxes
- Click delete action
- Confirmation dialog shows selected products
- Requires `products:delete` permission
- Soft delete (products marked as deleted, not removed from DB)

### Permissions

#### Required Permissions

- `products:view` - View product list (all users)
- `products:create` - See "Create Product" button
- `products:delete` - Delete products

#### Permission Gates

```typescript
<PermissionGate permission="products:create">
  <Button>Create Product</Button>
</PermissionGate>
```

### UI Components

#### Loading State

Skeleton loader while data loads:

```typescript
<React.Suspense fallback={<DataTableSkeleton />}>
  <ProductsTable promises={promises} />
</React.Suspense>
```

#### Data Table Component

Uses TanStack Table with:

- Server-side pagination
- Client-side filtering (for quick search)
- Row selection state
- Column visibility controls
- Global search across all columns

### Server-Side Processing

#### Query Performance

- Uses Prisma's efficient query builder
- Includes only necessary relations
- Implements pagination at database level
- Caches results to reduce database load

#### Response Format

```typescript
{
  data: ProductWithRelations[],  // Product records
  pageCount: number,            // Total pages
  totalCount: number             // Total records
}
```

### Common Use Cases

#### Find Specific Product

1. Use search bar to search by name/code/description
2. Apply filters to narrow results
3. Sort by relevant column
4. Click on product name to view details

#### Bulk Delete

1. Select products using checkboxes
2. Click delete action
3. Confirm deletion
4. Products are removed from view

#### Monitor Product Status

1. Filter by status (e.g., OUT_OF_STOCK)
2. Sort by updated date
3. View stock indicators
4. Take action on products needing attention

### Related Files

#### Page Component

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/page.tsx`

#### Data Table

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/_components/products-table.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/_components/products-table-columns.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/_components/products-table-action-bar.tsx`

#### Server Actions

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/_lib/queries.ts`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/_lib/actions.ts`

#### Validation

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/_lib/validations.ts`

### Next Steps

- Learn about [Product Creation](./product-creation.md)
- Learn about [Product Edit](./product-edit.md)
- Learn about [Product Details & Barcodes](./product-details.md)
