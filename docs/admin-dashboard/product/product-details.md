# Product Details & Barcode Generation

## Overview

The Product Details page provides a complete view of a single product, including inventory status, variant information, and tools for generating barcodes for inventory tracking.

## Purpose

This page helps you:

- See complete product information at a glance
- Understand current inventory levels
- View all product variants and their stock
- Generate QR codes for inventory tracking
- Print barcode labels for physical products
- Monitor product performance and history

## What You'll See

### Page Header

**Navigation Buttons**:

- **Back**: Return to product list
- **Share**: Share product link (if enabled)
- **Edit**: Modify product details
- **More options**: Additional actions menu

**Product Title**: Product name displayed prominently

**Status Badges**: Quick visual indicators showing:

- **Availability Status**: Available, Out of Stock, Draft, etc.
- **Category**: Which category the product belongs to
- **Product ID**: Internal reference number
- **Public/Private**: Whether product is visible to all sellers or restricted

### Main Content Area

#### Left Side: Image Gallery

Visual presentation of your product:

**Main Image**: Large display of the first product image

- Click to view in full screen
- Highest resolution version

**Thumbnail Gallery**: Grid of all product images

- Click any thumbnail to switch main image
- Shows all angles and details

**Product Video**: If video exists, shown as player

- Embed video directly in the page
- Play, pause, volume controls
- Fullscreen viewing

#### Right Side: Product Information

Tabbed interface with detailed product data:

**Overview Tab**: Basic product information

- Product name and code
- Description
- Provider information
- Category details
- Rating and quality score

**Pricing Tab**: Complete price breakdown

- Buy price, selling price, old price
- POS price and warehouse price
- Special seller pricing (if any)
- Price history

**Stock Tab**: Inventory summary

- Total stock across all locations
- Reserved stock (allocated to orders)
- Available stock (ready to ship)
- Stock by location (main warehouse, other warehouses)
- Stock trends and movements

**Variants Tab**: Variant overview

- Number of variants
- Variant types (color/size or custom)
- Stock levels per variant
- Variant-specific pricing

**Metadata Tab**: Additional information

- Creation and update dates
- System metadata
- Audit trail information

### Variants Table Section

Comprehensive table showing all product variants:

**Table Columns**:

1. **Variant**: Color/size or custom type (e.g., "Red-Large")
2. **SKU**: Unique variant code for reference
3. **Main Stock**: Quantity in primary warehouse
4. **Warehouse Stock**: Quantity in other locations
5. **Total Stock**: Combined inventory across all locations
6. **Reserved**: Quantity allocated to open orders
7. **Available**: Ready-to-ship quantity
8. **Barcodes**: Number of QR codes generated
9. **Status**: Active/inactive status
10. **Actions**: Buttons to manage stock, generate barcode, edit

**Table Features**:

- **Sorting**: Click column headers to sort
- **Filtering**: Search by variant name or SKU
- **Row Selection**: Select multiple variants for bulk actions
- **Pagination**: Navigate through many variants

### Stock Summary Card

Quick overview of product inventory:

**Key Metrics**:

- **Total Stock**: All inventory across all warehouses
- **Total Reserved**: Allocated to customer orders
- **Total Available**: Ready for new orders
- **Variant Count**: Number of different variants
- **Color Count**: Number of unique color options
- **Barcode Count**: Total QR codes generated
- **Warehouse Count**: Number of warehouses with stock

**Visual Indicators**:

- Stock levels shown as percentages or color-coded badges
- Alerts when stock is low
- Out-of-stock warnings prominently displayed

## Barcode Generation

### What Are Barcodes?

Barcodes (QR codes in this system) are:

- **Unique identifiers** for each product variant
- **Scannable codes** that link to products in the system
- **Inventory tracking tools** for stock management
- **Physical labels** attached to products for easy scanning

### Why Use Barcodes?

**Benefits**:

- **Accurate inventory**: Scan to instantly update stock levels
- **Quick lookups**: Scan QR code to see product details
- **Error prevention**: Eliminate manual entry mistakes
- **Efficiency**: Process many items quickly
- **Tracking**: Trace inventory movements over time
- **Loss prevention**: Know exactly what you have

### How Barcodes Work in This System

**Unique QR Codes**: Each variant assignment gets one unique QR code

- **Format**: Product code + variant ID + unique identifier
- **Example**: TSHIRT-ABC123-1712452800000
- **Stored in database**: System keeps record of all QR codes
- **Linked to product**: QR code identifies specific product variant

**Inventory Tracking**:

- Scan QR code to identify product
- Update stock levels instantly
- Track movements between locations
- Record transfers, sales, losses

### Generating QR Codes

#### Step 1: Select Variants

When you first open the barcode section, you'll see:

- List of all variant assignments for this product
- Variants without QR codes highlighted
- Variants with QR codes marked as "Has QR Code"

**Selection Options**:

- **Select All**: Click to select all variants without QR codes
- **Select Individually**: Click checkboxes to choose specific variants
- **Deselect All**: Clear selections and start over

**Display**:
Each variant shows:

- Color swatch (for color variants)
- Variant name and size
- SKU code
- Checkbox for selection
- Status indicator (has QR code or not)

#### Step 2: Generate QR Codes

After selecting variants:

1. Click "Generate QR Codes" button
2. System creates one unique QR code per selected variant
3. QR codes are stored in the database
4. Success message shows how many were generated
5. Variants update to show "Has QR Code" status

**What Happens**:

- Each selected variant gets one QR code
- QR code contains unique identifier
- System saves QR code data
- No duplicate QR codes are created

### Printing Barcode Labels

After QR codes are generated, you can print physical labels:

#### Step 1: Set Print Quantities

**Quantity Per QR Code**: How many labels to print for each QR code

- **Default**: 1 label per QR code
- **Custom**: Set different quantities per QR code
- **Range**: 1 to 500 labels per QR code
- **Purpose**: Print multiple labels if you have multiple physical items

**Quick Set Feature**:

- Select multiple QR codes
- Set a quantity (e.g., 10)
- Click "Apply" to set same quantity for all selected
- Saves time when setting quantities for many QR codes

#### Step 2: Filter and Select

**Filter Options**: Narrow down which QR codes to print

- **Color Filter**: Show only QR codes for specific colors
- **Size Filter**: Show only QR codes for specific sizes
- **Type Filter**: Show only QR codes for specific custom types
- **Value Filter**: Show only QR codes for specific values

**Selection Options**:

- **Select All**: Select all filtered QR codes for printing
- **Select Individually**: Click checkboxes to choose specific QR codes
- **Clear Selection**: Deselect all

**Display**:
Each QR code in the list shows:

- Checkbox for selection
- Color swatch (if applicable)
- Variant name and details
- Input field for quantity
- Selected state highlighting

#### Step 3: Print Labels

**Print All**: Print labels for all visible QR codes

- Uses quantities you've set
- Opens print dialog in new window
- Generates label for each quantity

**Print Selected**: Print labels only for checked QR codes

- Useful when you want specific variants only
- Saves paper and time
- Opens print dialog with selected items only

### Label Format and Appearance

**Thermal Label Specifications**:

- **Size**: 50mm x 25mm (standard thermal label)
- **Orientation**: Landscape (wider than tall)
- **Layout**: QR code on left, product info on right

**Label Content**:

```
┌────────────────────────────────────┐
│                                │
│   [QR Code - 48% of width]     │  Product Name
│                                │     SIZE
│   Product Info - 50% of width   COLOR
│                                │
└────────────────────────────────────┘
```

**QR Code Area** (left side):

- 21mm x 21mm square
- Contains unique identifier
- Scannable by any QR code reader
- High contrast for reliable scanning

**Product Info Area** (right side):

- **Product Name**: Bold, truncated if too long (e.g., "Cotton T-S...")
- **Size**: Large, bold, uppercase (e.g., "LARGE")
- **Color**: Medium, bold, uppercase (e.g., "RED")
- **Text Style**: Arial Black or similar bold font

### Printing Process

**What Happens When You Click Print**:

1. New browser window opens with print preview
2. System generates HTML for all labels
3. QR codes render as SVG graphics
4. Print dialog appears automatically
5. Select your thermal printer
6. Print labels

**Print Preview**:

- Shows exact layout of labels
- One label per page (50mm x 25mm)
- Preview QR codes as they'll print
- Verify before printing

**After Printing**:

- Labels are ready to attach to products
- Peel and stick on physical items
- Scan to verify QR codes work
- Update inventory when items are received

## Business Workflow Examples

### Scenario 1: New Product Arrival with QR Codes

1. **Create product**: Add new product with variants
2. **Generate QR codes**: Select all variants, generate codes
3. **Print labels**: Set quantity to match physical items
4. **Attach labels**: Stick labels on each physical item
5. **Scan to receive**: Scan QR codes when items arrive in warehouse
6. **Stock updated**: Inventory automatically updated

### Scenario 2: Restock Existing Product

1. **Go to product details**: Navigate to product page
2. **View stock levels**: Check current inventory
3. **Generate additional barcodes**: Create new QR codes for new items
4. **Print labels**: Print labels for restock quantity
5. **Scan on arrival**: Scan QR codes when new stock arrives
6. **Stock incremented**: Inventory increases automatically

### Scenario 3: Print Labels for Specific Variants

1. **Filter variants**: Use color/size filters to show only needed variants
2. **Select variants**: Choose variants you need labels for
3. **Set quantities**: Enter label quantity per variant (e.g., 50 each)
4. **Print selected**: Click "Print Selected" for only filtered items
5. **Attach and scan**: Apply labels and scan to verify

### Scenario 4: Reprint Damaged Labels

1. **Find product**: Go to product details page
2. **View existing QR codes**: See all generated codes
3. **Filter to specific variant**: Find the variant needing new labels
4. **Set quantity**: Enter number of labels needed
5. **Print selected**: Print only that QR code's labels
6. **Replace and verify**: Replace damaged labels, scan to confirm

## Inventory Management Tips

### Regular QR Code Management

- Generate QR codes when creating products
- Generate new codes when adding variants
- Print labels immediately after generation
- Keep backup of QR codes (screenshot or print)

### Stock Monitoring

- Check stock summary regularly
- Pay attention to low stock warnings
- Restock before running out
- Use barcodes for accurate tracking

### Label Quality

- Use high-quality thermal paper
- Ensure QR codes are clearly printed
- Test labels with your barcode scanner
- Replace worn or damaged labels
- Keep label printer maintained

### Scanning Best Practices

- Scan QR codes when items move locations
- Scan when items arrive (receiving)
- Scan when items ship (outbound)
- Scan for inventory counts (stock takes)
- Scan to identify products (lookups)

## Understanding Stock Levels

### Total Stock

- All physical inventory across all warehouses
- Includes main warehouse and other locations
- Shows how much you have in total

### Reserved Stock

- Quantity allocated to open customer orders
- Not available for new orders
- Decreases when orders ship

### Available Stock

- Total stock minus reserved stock
- Ready for new customer orders
- The quantity sellers can order
- Most important metric for planning

### Location-Based Stock

- **Main Stock**: Primary warehouse inventory
- **Warehouse Stock**: Other locations (satellite warehouses)
- Track stock per location for better planning
- Transfer stock between locations as needed

## Common Issues

### QR Code Generation Fails

**Possible causes**:

- Network connection issue
- System error
- Variant not found
- Permission denied

**Solutions**:

- Check internet connection
- Refresh the page and try again
- Verify variant assignments exist
- Check your permissions

### Print Window Won't Open

**Possible causes**:

- Popup blocker enabled
- Browser security settings
- JavaScript disabled

**Solutions**:

- Allow popups for this site
- Check browser settings
- Try different browser
- Temporarily disable popup blocker

### QR Codes Won't Scan

**Possible causes**:

- Print quality too low
- QR code too small
- Paper not suitable
- Label damaged

**Solutions**:

- Use higher print quality settings
- Ensure correct label size (50mm x 25mm)
- Use thermal paper for best results
- Clean scanner lens
- Test with multiple scanners

### Stock Summary Wrong

**Possible causes**:

- Cache not refreshed
- Database sync delay
- Concurrent updates by other users

**Solutions**:

- Refresh the page
- Wait for database sync
- Check if other users updated stock
- Contact support if issue persists

## Data Integrity

### QR Code Uniqueness

- Each QR code is globally unique in the system
- Based on product code, variant ID, and timestamp
- No duplicate QR codes can exist
- System prevents duplicate generation

### Inventory Accuracy

- Stock levels updated via QR code scanning
- Reserved stock tracked separately from physical stock
- Location-based stock tracking
- Real-time inventory updates

### Tracking History

- All QR code scans are logged
- Movement history preserved
- Audit trail for inventory
- Can trace when items moved

## Permissions

This page requires:

- **products:view**: View product details and inventory
- **products:update**: Generate barcodes and manage stock

## Tips for Efficient Use

### Quick Navigation

- Use tabbed interface to jump between information sections
- Use search within variants table to find specific variants
- Use keyboard navigation if enabled

### Regular Reviews

- Check product details regularly for accuracy
- Review stock levels and plan restocks
- Generate QR codes for new items immediately
- Print labels in batches for efficiency

### Barcode Management

- Generate QR codes as soon as product is created
- Print labels right after generation
- Keep backup of QR codes
- Label physical items promptly
- Scan to verify labels work

## Next Steps

- Return to [Product List](./product-list.md) to browse products
- Edit product information on the [Product Edit](./product-edit.md) page
- Create new products on the [Product Creation](./product-creation.md) page
