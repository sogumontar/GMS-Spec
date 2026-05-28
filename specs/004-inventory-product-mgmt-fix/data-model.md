# Data Model: Inventory & Product Management Enhancements

**Date**: 2026-05-20

## Entities

### Product

Represents an item available in the inventory.

-   **id**: Unique identifier for the product (string, e.g., `prod-001`)
-   **name**: Name of the product (string)
-   **sku**: Stock Keeping Unit (string, unique)
-   **category**: Product category (string, e.g., `Electronics`, `Peripherals`)
-   **price**: Unit price of the product (number, currency)
-   **stockLevel**: Current quantity of the product in stock (number)
-   **status**: Current stock status (string, e.g., `In Stock`, `Low Stock`, `Out of Stock`)
-   **imageUrl**: URL or path to the product image (string, optional)
-   **description**: Detailed description of the product (string, optional)

### Inventory Metric

Represents aggregated data for inventory overview.

-   **totalProducts**: Total count of all distinct products (number)
-   **lowStockAlerts**: Number of products with stock below a predefined threshold (number)
-   **outOfStock**: Number of products with zero stock (number)
-   **totalValue**: Aggregate monetary value of all in-stock products (number, currency)

## Relationships

-   `Inventory Metric` data is derived from an aggregation of `Product` entities.

## Validation Rules (Examples)

-   `Product.name`: Required, min length 3, max length 100.
-   `Product.sku`: Required, unique, alphanumeric.
-   `Product.price`: Required, greater than 0.
-   `Product.stockLevel`: Required, non-negative integer.
