EXPECTED PARSING RESULTS
=======================

1. CSV FILE PARSING RESULTS (employees.csv)
------------------------------------------
Total Records: 5 employees

Expected Data Structure:
Each record should contain: [id, first_name, last_name, email, department, salary]

Example Output:
Record 1: [1, John, Smith, john.smith@company.com, Engineering, 75000]
Record 2: [2, Sarah, Johnson, sarah.j@company.com, Marketing, 65000]
Record 3: [3, Michael, Brown, m.brown@company.com, Sales, 70000]
Record 4: [4, Emily, Davis, e.davis@company.com, Engineering, 78000]
Record 5: [5, James, Wilson, j.wilson@company.com, HR, 62000]

Department Summary:
- Engineering: 2 employees
- Marketing: 1 employee
- Sales: 1 employee
- HR: 1 employee

2. JSON FILE PARSING RESULTS (products.json)
------------------------------------------
Total Products: 3 items

Expected Data Structure:
- Root element: "products" (JSONArray)
- Each product is a JSONObject containing:
  * id (String)
  * name (String)
  * category (String)
  * price (Double)
  * specifications (JSONObject)
  * inStock (Boolean)

Example Output:
Product 1:
- ID: P001
- Name: Laptop Pro X
- Category: Electronics
- Price: 1299.99
- Specifications:
  * processor: Intel i7
  * ram: 16GB
  * storage: 512GB SSD
- In Stock: true

Product 2:
- ID: P002
- Name: Wireless Headphones
- Category: Audio
- Price: 199.99
- Specifications:
  * type: Over-ear
  * batteryLife: 30 hours
  * bluetooth: 5.0
- In Stock: true

Product 3:
- ID: P003
- Name: Smart Watch
- Category: Wearables
- Price: 299.99
- Specifications:
  * display: AMOLED
  * waterproof: true
  * batteryLife: 48 hours
- In Stock: false

Summary Statistics:
- Total Products: 3
- In Stock Products: 2
- Out of Stock Products: 1
- Price Range: $199.99 - $1299.99
- Categories: Electronics, Audio, Wearables