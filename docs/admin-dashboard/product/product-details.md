# Product Details & Barcodes

## Overview

View complete product information, inventory status, and generate barcodes for tracking.

---

## What You'll See

### Page Header

| Element           | Description                            |
| ----------------- | -------------------------------------- |
| **Back Button**   | Return to product list                 |
| **Share Button**  | Share product link                     |
| **Edit Button**   | Modify product details                 |
| **Product Title** | Product name                           |
| **Status Badges** | Availability, category, public/private |
| **ID**            | Product identifier                     |

### Product Information (Right Side)

Tabbed interface with the following tabs:

| Tab          | What It Shows                                       |
| ------------ | --------------------------------------------------- |
| **Overview** | Name, code, description, provider, category, rating |
| **Pricing**  | All prices and special seller pricing               |
| **Stock**    | Inventory summary and data                          |
| **Variants** | Variant overview                                    |
| **Metadata** | Creation date, update date, system info             |

### Variants Table

Shows all product variants:

| Column              | Description                          |
| ------------------- | ------------------------------------ |
| **Variant**         | Color/size or custom type            |
| **SKU**             | Unique variant code                  |
| **Main Stock**      | Primary warehouse quantity           |
| **Warehouse Stock** | Other locations                      |
| **Total Stock**     | Combined inventory                   |
| **Reserved**        | Allocated to orders                  |
| **Available**       | Ready to ship                        |
| **Barcodes**        | Number of QR codes                   |
| **Status**          | Active/inactive                      |
| **Actions**         | Manage stock, generate barcode, edit |

The table is sortable and filterable.

### Stock Summary

Quick metrics:

| Metric              | What It Means                       |
| ------------------- | ----------------------------------- |
| **Total Stock**     | All inventory across all warehouses |
| **Total Reserved**  | Allocated to customer orders        |
| **Total Available** | Ready for new orders                |
| **Variant Count**   | Number of different variants        |
| **Color Count**     | Number of unique colors             |
| **Barcode Count**   | Total QR codes generated            |
| **Warehouse Count** | Number of warehouses with stock     |

---

## Barcode Generation

### What Are Barcodes?

Unique QR codes for inventory tracking.

### Why Use Barcodes?

| Benefit                | Description                           |
| ---------------------- | ------------------------------------- |
| **Accurate Inventory** | Scan to instantly update stock levels |
| **Quick Lookups**      | Scan QR code to see product details   |
| **Error Prevention**   | Eliminate manual entry mistakes       |
| **Efficiency**         | Process many items quickly            |
| **Tracking**           | Trace inventory movements             |

### Generate QR Codes

1. Go to the **Barcode Generation** section
2. **Select variants** from the list (those without QR codes are highlighted)
3. Click **Generate QR Codes** button

The system creates one unique QR code per selected variant.

### Print Barcode Labels

| Action                   | Description                                         |
| ------------------------ | --------------------------------------------------- |
| **Set Print Quantities** | How many labels per QR code (1-500, default: 1)     |
| **Filter Options**       | Filter by color, size, or custom type               |
| **Selection**            | Select all filtered QR codes or select individually |
| **Print All**            | Print labels for all visible QR codes               |
| **Print Selected**       | Print labels only for checked QR codes              |

### Label Format

- **Size**: 50mm x 25mm (thermal label)
- **Layout**: QR code (left), product info (right)

**Label Content:**

```
┌─────────────────────────────┐
│   [QR Code]   Product Name  │
│                  Size       │
│                  Color      │
└─────────────────────────────┘
```

> **Tip**: Use thermal printer for best results.

---

## Permissions

| Action               | Required Permission |
| -------------------- | ------------------- |
| View product details | `products:view`     |
| Generate barcodes    | `products:update`   |
| Manage stock         | `products:update`   |

---

## Next Steps

- 📋 Return to [Product List](./product-list.md) to view all products
- ✏️ Edit product details on the [Product Edit](./product-edit.md) page
- 📦 Create new products on the [Product Creation](./product-creation.md) page
