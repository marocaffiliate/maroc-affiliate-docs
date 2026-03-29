# Product Details & Barcode Generation

## Overview

The Product Details page provides comprehensive information about a single product, including inventory data, variant details, and barcode generation for inventory tracking.

## Location

`/src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/page.tsx`

## Purpose

Display complete product information with:

- Product overview and metadata
- Image gallery and media
- Stock summary and inventory data
- Variant details table
- QR code generation and printing

## Page Structure

### Header Section

#### Navigation

- **Back button**: Return to product list
- **Share button**: Share product link
- **Edit button**: Edit product information
- **More options**: Additional actions menu

#### Product Title and Badges

- **Product name**: Large, bold title
- **Status badge**: Current availability (Available, Out of Stock, etc.)
- **Category badge**: Product category
- **ID badge**: Product ID for reference
- **Public/Private badge**: Visibility status

### Main Content Grid

#### Image Gallery (Left Column)

- **Product images**: Display first image as main, others as thumbnails
- **Product video**: If video exists, shown as embed or player
- **Responsive layout**: Stacks vertically on mobile, side-by-side on desktop
- **Lightbox**: Click to view full-size images

#### Product Information (Right Column)

Contains tabbed information:

- **Overview**: Basic product details
- **Pricing**: Price breakdown
- **Stock**: Inventory summary
- **Variants**: Variant assignments
- **Metadata**: Additional product data

### Variants Table Section

#### Variant Information Table

Shows all variant assignments:

- **Variant name**: Color/size or custom type
- **SKU code**: Unique variant identifier
- **Stock levels**: Main stock and warehouse stock
- **Barcodes**: QR code count
- **Status**: Active/inactive status
- **Actions**: Edit, generate barcode, manage stock

### Barcode Generator Section

#### QR Code Generation

Generate unique QR codes for each variant assignment:

- **One QR code per variant assignment**
- **Unique identifier** for inventory tracking
- **Stored in database** for reference
- **Printable labels** for physical products

## Data Fetching

### Parallel Queries

```typescript
const [product, stockSummary] = await Promise.all([
  getProductById(productId),
  getProductStockSummary(productId),
]);
```

### Product Data

```typescript
{
  id: number,
  name: string,
  code: string,
  description: string,
  status: string,
  variantType: "NONE" | "COLOR_SIZE" | "CUSTOM",
  isPublic: boolean,
  category: Category,
  provider: User,
  images: string[],
  video: string[],
  buyPrice: number,
  sellingPrice: number,
  posPrice: number,
  wareHousePrice: number,
  ratingStars: number,
  minimumSellerType: string,
  allowedSellers: User[],
  productVariantAssignments: ProductVariantAssignment[],
  specialSellerPrices: SpecialSellerPrice[],
  barcodes: Barcode[]
}
```

### Stock Summary

```typescript
{
  totalStock: number,           // Total quantity across all locations
  totalReserved: number,        // Reserved for orders
  totalAvailable: number,        // Available for sale
  variantCount: number,         // Number of variant assignments
  colorCount: number,           // Number of unique colors
  barcodeCount: number,         // Total QR codes generated
  warehouseCount: number        // Number of warehouses with stock
}
```

## Barcode Generation System

### Purpose

Generate unique QR codes for inventory tracking:

- **Each variant gets one QR code**
- **QR code contains unique identifier**
- **Used for stock scanning**
- **Links to product/variant in system**

### QR Code Format

```typescript
Format: {
  ProductCode;
}
-{ VariantID } - { Timestamp } - { Index };

Example: TSHIRT - ABC123 - 1712452800000 - 0;
```

### Generation Process

#### Step 1: Select Variant Assignments

- List all variant assignments without QR codes
- Select assignments to generate codes for
- Filter by color/size/type as needed
- Select all or select individually

#### Step 2: Generate QR Codes

- Click "Generate QR Codes" button
- System generates one QR code per selected assignment
- QR codes stored in database with assignment reference
- Success message shows count generated

#### Step 3: Print Labels

- Set print quantity per QR code (default: 1)
- Filter QR codes by color/size/type
- Select specific QR codes or print all
- Print thermal labels (50mm x 25mm format)

### Label Specifications

#### Thermal Label Format

- **Dimensions**: 50mm x 25mm
- **Orientation**: Landscape
- **Layout**: QR code left, product info right

#### Label Content

```
┌────────────────────────────────────┐
│                                │
│   [QR Code Area - 48% width]  │  Product Name
│                                │    SIZE
│   Product Information - 50% width  COLOR
│                                │
└────────────────────────────────────┘
```

#### Label Details

- **QR Code**: 21mm x 21mm, unique identifier
- **Product Name**: 8px bold, truncated if long
- **Size**: 16px black, uppercase, letter spacing
- **Color**: 9px bold, uppercase, letter spacing

### Print Features

#### Quantity Control

- **Default**: 1 label per QR code
- **Custom**: Set quantity 1-500 per QR code
- **Quick Set**: Apply same quantity to selected QR codes
- **Individual**: Set different quantities per QR code

#### Filtering

- **Color filter**: Show only specific colors
- **Size filter**: Show only specific sizes
- **Type/Value filter**: For custom variants
- **Combine filters**: Multiple filters active simultaneously

#### Selection

- **Select All**: Select all visible QR codes
- **Select Individually**: Click checkboxes to select
- **Clear Selection**: Deselect all
- **Print Selected**: Print only selected QR codes
- **Print All**: Print all QR codes (if none selected)

#### Print Summary

- **Total labels**: Sum of all quantities
- **Selected count**: Number of QR codes selected
- **Total selected labels**: Labels from selected QR codes

### Technical Implementation

#### QR Code Generation

```typescript
const generateBarcodes = async () => {
  for (const assignmentId of selectedAssignments) {
    const variant = variants.find((v) => v.assignmentId === assignmentId);

    const timestamp = Date.now();
    const uniqueCode = `${product.code}-${variant.id}-${timestamp}`;

    const barcodeData = {
      barcodeValue: uniqueCode,
      productId: product.id,
      productVariantAssignmentId: assignmentId,
      currentLocation: "MAIN_STOCK",
      trackingType: "STANDARD",
    };

    await db.barcode.create({
      data: barcodeData,
    });
  }
};
```

#### Print Layout

Generated HTML with inline CSS:

```html
<!DOCTYPE html>
<html>
  <head>
    <style>
      @page {
        size: 50mm 25mm;
        margin: 0;
      }
      .label {
        width: 50mm;
        height: 25mm;
        page-break-after: always;
        display: flex;
      }
      .qr-placeholder {
        width: 21mm;
        height: 21mm;
      }
    </style>
    <script src="qrcode-generator.js"></script>
  </head>
  <body>
    <div class="label">
      <div class="qr-placeholder" data-code="UNIQUE-CODE"></div>
      <div class="info-section">
        <div class="product-name">Product Name</div>
        <div class="size-display">SIZE</div>
        <div class="color-display">COLOR</div>
      </div>
    </div>
  </body>
</html>
```

#### QR Code Rendering

Uses `qrcode-generator` library:

- Client-side QR generation
- SVG format for high quality
- Configurable size and error correction
- Renders in new print window

## Stock Overview

### Stock Summary Card

Shows key inventory metrics:

- **Total Stock**: All inventory across locations
- **Total Reserved**: Reserved for customer orders
- **Total Available**: Ready for sale
- **Variant Count**: Number of variant assignments
- **Color Count**: Unique color variants
- **Barcode Count**: Total QR codes generated
- **Warehouse Count**: Warehouses with stock

### Stock by Location

- **Main Stock**: Primary warehouse inventory
- **Warehouse Stock**: Multiple warehouse locations
- **Reserved Stock**: Allocated to orders
- **Available Stock**: Ready for fulfillment

## Variant Details Table

### Table Columns

1. **Variant**: Color/size or custom type
2. **SKU**: Variant code
3. **Main Stock**: Primary warehouse quantity
4. **Warehouse Stock**: Other locations
5. **Total Stock**: Combined stock
6. **Reserved**: Reserved for orders
7. **Available**: Ready for sale
8. **Barcodes**: QR code count
9. **Status**: Active/inactive
10. **Actions**: Manage stock, generate barcode

### Table Features

- **Sortable columns**: Click to sort
- **Filter variants**: Search by name/SKU
- **Status indicators**: Color-coded badges
- **Bulk actions**: Select multiple variants
- **Row expansion**: View variant details

## Media Display

### Image Gallery

- **Main image**: Large display of first image
- **Thumbnails**: Grid of all images
- **Navigation**: Click thumbnails to switch main image
- **Fullscreen**: Click to view fullscreen
- **Responsive**: Adapts to screen size

### Video Player

- **Embed**: Native HTML5 video player
- **Controls**: Play, pause, volume, fullscreen
- **Responsive**: Adapts to container
- **Autoplay**: Starts when viewed

## Technical Implementation

### Component Hierarchy

```
ProductDetailPage (Server)
  ├── ProductImageGallery
  ├── ProductDetailTabs
  │   ├── Overview Tab
  │   ├── Pricing Tab
  │   ├── Stock Tab
  │   └── Metadata Tab
  ├── ProductVariantsTable
  └── BarcodeGenerator
      ├── QR Code Generation Card
      └── Generated QR Codes Card
```

### Key Components

#### ProductImageGallery

Displays product images and video:

- Image carousel/main display
- Thumbnail grid
- Video player
- Lightbox functionality

#### ProductDetailTabs

Tabbed interface for product information:

- Overview: Basic product details
- Pricing: Price breakdown
- Stock: Inventory data
- Metadata: Additional fields

#### ProductVariantsTable

Shows all variant assignments:

- Sortable table
- Stock levels per variant
- QR code counts
- Action buttons

#### BarcodeGenerator

QR code generation and printing:

- Select variants to generate
- Generate QR codes
- Set print quantities
- Filter and select for printing
- Print thermal labels

#### BarcodeRenderer

Renders QR codes using library:

- SVG-based rendering
- Configurable size
- Error correction level
- Display value option

## Permissions

### Required Permissions

- `products:view` - View product details
- `products:update` - Generate barcodes

### Permission Gates

```typescript
<PermissionGate permission="products:update">
  <Button>Generate Barcodes</Button>
</PermissionGate>
```

## Caching Strategy

### Product Detail Cache

```typescript
{
  revalidate: 10,  // 10 seconds
  tags: [`product-${id}`, "products", "stock"]
}
```

### Cache Tags

- `product-${id}`: Specific product
- `products`: All products
- `stock`: Inventory data

## Best Practices

### QR Code Generation

- Generate QR codes after product creation
- Generate one per variant assignment
- Print labels immediately after generation
- Store labels in safe location
- Keep backup of QR codes

### Label Printing

- Use thermal printer (50mm x 25mm)
- Test print settings first
- Print in batches for efficiency
- Verify QR code quality
- Attach labels to products immediately

### Stock Management

- Monitor stock levels regularly
- Use barcodes for inventory scanning
- Update stock after movements
- Track reserved vs available stock
- Maintain accurate counts

### Label Quality

- Use high-quality thermal paper
- Ensure QR codes are scannable
- Test with barcode scanner
- Keep print heads clean
- Replace worn labels

## Common Issues

### QR Code Generation Fails

**Possible causes**:

- Network error
- Database connection issue
- Variant assignment not found
- Permission denied

**Solutions**:

- Check network connection
- Verify permissions
- Refresh page and retry
- Check variant assignments exist

### Print Window Not Opening

**Possible causes**:

- Popup blocker enabled
- Browser security setting
- JavaScript disabled

**Solutions**:

- Allow popups for this site
- Check browser settings
- Use different browser
- Disable popup blocker temporarily

### QR Codes Not Scannable

**Possible causes**:

- Print quality issue
- QR code too small
- Paper not suitable
- Print head dirty

**Solutions**:

- Use higher print quality
- Ensure correct label size
- Use thermal paper
- Clean print heads
- Test with scanner

### Stock Summary Incorrect

**Possible causes**:

- Cache not refreshed
- Database sync delay
- Concurrent updates

**Solutions**:

- Refresh page
- Check database directly
- Wait for sync
- Contact support

## Data Integrity

### QR Code Uniqueness

- Each QR code is globally unique
- Based on product code, variant ID, timestamp
- No duplicate QR codes in system
- Stored in database with references

### Barcode Tracking

- Each barcode has current location
- Tracks movement: MAIN_STOCK → WAREHOUSE → SOLD
- History of movements preserved
- Can trace inventory items

### Stock Accuracy

- Stock levels updated via barcodes
- Reserved stock tracked separately
- Warehouse stocks distinguished
- Real-time inventory data

## Related Files

### Page Components

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/page.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_components/product-image-gallery.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_components/product-detail-tabs.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_components/product-variants-table.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_components/barcode-generator.tsx`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_components/barcode-renderer.tsx`

### Server Actions

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_lib/queries.ts`
- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/_lib/actions.ts`

### Types

- `src/app/[lang]/(dashboard-layout)/dashboards/admin/products/[id]/types.ts`

## Next Steps

- Learn about [Product List](./product-list.md)
- Learn about [Product Creation](./product-creation.md)
- Learn about [Product Edit](./product-edit.md)
