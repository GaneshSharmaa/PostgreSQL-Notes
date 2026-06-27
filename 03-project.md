# Project

### **Q:** Create a database named Flipkart_db and then create a table with:

- Product ID → serial
- Name → string
- sku_code 8-digit code → string
- Maximum price → number
- Stock_quantity → number (greater than 0)
- Is available → boolean (by default True)
- Category → string (not null)
- Added_on → date
- Last_update → date

**Solution:**

First let us create a database for this `flipkart_db`.

```sql
CREATE DATABASE FLIPKART_DB;
```

Switching to `flipkart_db`:

```sql
\c flipkart_db
```

Then creating a table `PRODUCT_DETAILS`.

```sql
CREATE TABLE PRODUCT_DETAILS (
    PRODUCT_ID SERIAL PRIMARY KEY,
    NAME VARCHAR(100) NOT NULL,
    SKU_CODE CHAR(8) UNIQUE NOT NULL CHECK (CHAR_LENGTH(SKU_CODE) = 8),
    MAX_PRICE NUMERIC(10, 2) DEFAULT 0 CHECK (MAX_PRICE >= 0),
    STOCK_QUANTITY INT DEFAULT 0 CHECK (STOCK_QUANTITY >= 0),
    IS_AVAIL BOOLEAN DEFAULT TRUE,
    CATEGORY VARCHAR(20) NOT NULL,
    ADDED_ON DATE DEFAULT CURRENT_DATE,
    LAST_UPDATE TIMESTAMP DEFAULT NOW()
);
```

Checking if all the columns have been created properly or not:

```sql
SELECT * FROM PRODUCT_DETAILS;
```

Adding records to the table:

```sql
INSERT INTO PRODUCT_DETAILS
(NAME, SKU_CODE, MAX_PRICE, STOCK_QUANTITY, IS_AVAIL, CATEGORY)
VALUES
('Wireless Mouse',      'WM100001',  799,   120, TRUE,  'Electronics'),
('Mechanical Keyboard', 'MK100002', 3499,    45, TRUE,  'Electronics'),
('Gaming Headset',      'GH100003', 2799,    30, TRUE,  'Electronics'),
('USB-C Charger',       'UC100004', 1499,    80, TRUE,  'Accessories'),
('Laptop Stand',        'LS100005', 1899,    25, TRUE,  'Accessories'),
('Office Chair',        'OC100006', 8999,    10, TRUE,  'Furniture'),
('Study Table',         'ST100007', 6499,     8, TRUE,  'Furniture'),
('Water Bottle',        'WB100008',  499,   150, TRUE,  'Kitchen'),
('Coffee Mug',          'CM100009',  299,   200, TRUE,  'Kitchen'),
('Bluetooth Speaker',   'BS100010', 2499,    40, TRUE,  'Electronics'),
('LED Desk Lamp',       'DL100011', 1299,    60, TRUE,  'Lighting'),
('Smart Watch',         'SW100012', 6999,    18, TRUE,  'Wearables'),
('Fitness Band',        'FB100013', 2999,    35, TRUE,  'Wearables'),
('Power Bank',          'PB100014', 1799,    50, TRUE,  'Accessories'),
('Notebook Set',        'NS100015',  399,   100, TRUE,  'Stationery'),
('Ball Pen Pack',       'BP100016',  199,   300, TRUE,  'Stationery'),
('Travel Backpack',     'TB100017', 2499,    22, TRUE,  'Bags'),
('Yoga Mat',            'YM100018',  999,    40, TRUE,  'Fitness'),
('Running Shoes',       'RS100019', 4999,    15, FALSE, 'Footwear'),
('Digital Calculator',  'DC100020',  899,    55, TRUE,  'Stationery');
```

