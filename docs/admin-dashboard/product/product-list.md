# Product List Page

## Overview

The Product List page is your main dashboard for viewing, searching, and managing all products in the marocAffiliate platform. Think of it as your central inventory control center.

## Purpose

This page helps you:

- See all products at a glance
- Find specific products quickly
- Filter products by various criteria
- Understand product status and stock levels
- Take bulk actions on multiple products
- Navigate to product details or edit pages

## What You'll See

### Main Table

A clean, organized table showing all products with key information:

**Image**: Product thumbnail (first image from gallery)
**Name & Code**: Product name with unique code below it
**Category**: Which category the product belongs to
**Status**: Current availability (Available, Out of Stock, Draft, etc.)
**Variant Type**: How product variants are organized (None, Color/Size, Custom)
**Variants Count**: How many different variants exist for this product
**Stock Indicators**: Visual badges showing stock levels
**Selling Price**: Standard price for customers
**POS Price**: Price for in-store sales
**Actions**: Quick buttons to edit or delete the product

### Pagination

Products are shown in pages (default: 10 per page). You can:

- Navigate between pages using Previous/Next buttons
- Change how many products per page (10, 25, 50, 100)
- Jump to a specific page number

## How to Use This Page

### Finding Products

#### Quick Search

Use the search bar at the top to find products by:

- **Product name** (e.g., "T-shirt", "Jeans")
- **Product code** (e.g., "TSHIRT-ABC123")
- **Description** (e.g., "cotton", "summer")

The search looks across all these fields simultaneously and shows matching products.

#### Advanced Filters

Narrow down products using these filters:

**Status Filter**: Show only products with specific status

- **Available**: Ready to sell
- **Out of Stock**: Currently out of inventory
- **Draft**: Not yet published
- **Other**: Other status types

**Category Filter**: Show products from specific categories (e.g., "Clothing", "Electronics")

**Variant Type Filter**: Show products by variant system

- **None**: Single-SKU products
- **Color/Size**: Products with color and size options
- **Custom**: Products with custom variant types

**Seller Type Filter**: Show products based on minimum seller requirement

- **Normal**: All sellers can see
- **Pro**: Only Pro sellers can see
- **VIP**: Only VIP sellers can see

**Public/Private Filter**: Show visibility

- **Public**: Available to all eligible sellers
- **Private**: Available only to selected sellers

**Date Range Filter**: Show products created within a specific time period

- **Start Date**: From when (inclusive)
- **End Date**: To when (inclusive)

### Sorting Products

Click any column header to sort by that column:

- **Click once**: Sort ascending (A-Z, low to high)
- **Click again**: Sort descending (Z-A, high to low)
- **Default**: Sorted by "Last Updated" (newest first)

Useful sorting scenarios:

- Sort by **Name** to find products alphabetically
- Sort by **Selling Price** to see highest/lowest prices
- Sort by **Variants Count** to find complex products
- Sort by **Status** to focus on out-of-stock items

### Selecting Products

#### Individual Selection

Click the checkbox next to each product to select it. Selected products are highlighted.

#### Select All

Click the checkbox in the column header to select all products on the current page.

#### Bulk Selection

Selected products persist across page changes, so you can navigate through multiple pages and select products from each.

### Taking Actions

#### View Product Details

Click on the product name or image to go to the Product Details page where you can see:

- Full product information
- All variants and stock levels
- Generate barcodes
- View complete history

#### Edit Product

Click the "Edit" button (pencil icon) to modify:

- Product information (name, description, etc.)
- Pricing
- Variants
- Images and media
- Seller access

#### Delete Product

Click the "Delete" button (trash icon) to remove a product. You'll see a confirmation dialog showing:

- Product name
- Number of variants
- Confirmation message

**Note**: Deleting a product is permanent and removes all associated data.

#### Bulk Delete

After selecting multiple products, click the delete button to remove all selected products at once. You'll see a summary of what will be deleted.

## Business Workflow Examples

### Scenario 1: Find Out-of-Stock Products to Restock

1. Click on the **Status** filter
2. Select **"Out of Stock"**
3. Click "Apply Filters"
4. Review the list of products needing restock
5. Click on each product to view details and manage inventory

### Scenario 2: Review All Clothing Products

1. Click on the **Category** filter
2. Select **"Clothing"**
3. Click "Apply Filters"
4. Browse through clothing products
5. Use sorting to find specific items (e.g., by name or price)

### Scenario 3: Identify Recently Added Products

1. Click on the **"Last Updated"** column header to sort descending
2. The newest products appear at the top
3. Review recent additions
4. Take action on products that need attention

### Scenario 4: Clean Up Old Draft Products

1. Click on the **Status** filter
2. Select **"Draft"**
3. Sort by **"Last Updated"** descending
4. Review old drafts
5. Either complete the product details or delete unused drafts

## Understanding Product Status

### Available

Product is in stock and ready to sell. Sellers can view and order this product.

### Out of Stock

Product has no available inventory. Sellers can still see it but cannot order until restocked.

### Draft

Product is not yet published. Only admins can see and edit it. Sellers cannot view or order it.

### Other Statuses

Additional statuses may exist depending on your business needs (e.g., "Discontinued", "Coming Soon").

## Understanding Stock Indicators

The product list shows stock badges to help you identify inventory issues:

**Green**: Good stock levels (available)
**Yellow**: Low stock (consider restocking)
**Red**: Out of stock (urgent restock needed)
**Gray**: No stock tracking for this product

## Permissions

This page requires **products:view** permission. All admin users typically have this permission.

Additional actions require:

- **products:create**: See "Create Product" button
- **products:edit**: Edit products
- **products:delete**: Delete products

## Tips for Efficient Use

### Quick Navigation

- Use keyboard shortcuts (if enabled) to navigate quickly
- Bookmark frequently used filters as browser shortcuts
- Use browser's "Find" (Ctrl+F) to search within the current view

### Monitor Regularly

- Check the product list daily for stock issues
- Review out-of-stock items and plan restocks
- Monitor recently added products for completeness

### Bulk Operations

- Use bulk delete carefully (double-check selections)
- Consider export/import for large-scale changes
- Use filters to reduce bulk operation scope

### Filter Combinations

- Combine multiple filters for precise results (e.g., "Clothing" + "Out of Stock")
- Clear filters individually or reset all at once
- Save frequently used filter combinations as bookmarks

## Common Use Cases

### Daily Inventory Check

1. Filter by **Status: Out of Stock**
2. Review which products need restocking
3. Navigate to product details to manage stock
4. Order restocks as needed

### Product Catalog Review

1. Clear all filters
2. Sort by **Name** alphabetical
3. Browse through all products
4. Check for consistency in naming, pricing, categorization
5. Make notes for cleanup if needed

### Price Review

1. Clear all filters except **Category**
2. Sort by **Selling Price** descending
3. Review most expensive products
4. Check for pricing errors or inconsistencies
5. Edit as needed

### New Product Audit

1. Filter by **Date Range: Last 7 Days**
2. Sort by **Creation Date** descending
3. Review all recently added products
4. Verify completeness (images, descriptions, pricing)
5. Publish any incomplete drafts

## Next Steps

- Learn about [Product Creation](./product-creation.md)
- Learn about [Product Edit](./product-edit.md)
- Learn about [Product Details & Barcodes](./product-details.md)
