COMPREHENSIVE PARSING GUIDE AND VALIDATION CRITERIA
================================================

1. CSV FILE VALIDATION (employees.csv)
------------------------------------
File Format Requirements:
- UTF-8 encoding
- Comma-separated values
- No quoted fields
- No empty lines
- Headers in first row

Data Type Specifications:
1. id: Integer
   - Must be positive
   - Must be unique
   - No gaps in sequence

2. first_name: String
   - Non-empty
   - Only alphabetical characters
   - First letter capitalized

3. last_name: String
   - Non-empty
   - Only alphabetical characters
   - First letter capitalized

4. email: String
   - Valid email format (xxx@xxx.xxx)
   - Must contain '@company.com'
   - No spaces allowed

5. department: String
   - Must match valid departments: [Engineering, Marketing, Sales, HR]
   - Case sensitive

6. salary: Integer
   - Must be positive
   - Range: 50000-100000

Validation Checks:
- All fields must be present (6 columns)
- No trailing/leading whitespace
- No duplicate employee IDs
- No duplicate email addresses

Expected Data Structure in Java:
```java
class Employee {
    private int id;
    private String firstName;
    private String lastName;
    private String email;
    private String department;
    private int salary;
}

// Parsed result should be:
List<List<String>> rawData;  // Direct CSV parse
// or
List<Employee> employees;    // Mapped to objects
```

2. JSON FILE VALIDATION (products.json)
------------------------------------
File Format Requirements:
- UTF-8 encoding
- Valid JSON structure
- Pretty printed (formatted)
- Root element must be object

Schema Validation:
```json
{
  "type": "object",
  "required": ["products"],
  "properties": {
    "products": {
      "type": "array",
      "items": {
        "type": "object",
        "required": ["id", "name", "category", "price", "specifications", "inStock"],
        "properties": {
          "id": {
            "type": "string",
            "pattern": "^P\\d{3}$"
          },
          "name": {
            "type": "string",
            "minLength": 3
          },
          "category": {
            "type": "string",
            "enum": ["Electronics", "Audio", "Wearables"]
          },
          "price": {
            "type": "number",
            "minimum": 0
          },
          "specifications": {
            "type": "object",
            "minProperties": 1
          },
          "inStock": {
            "type": "boolean"
          }
        }
      }
    }
  }
}
```

Expected Data Structure in Java:
```java
class Product {
    private String id;
    private String name;
    private String category;
    private double price;
    private Map<String, Object> specifications;
    private boolean inStock;
}

class ProductCatalog {
    private List<Product> products;
}
```

Validation Checks:
- Product IDs must start with 'P' followed by 3 digits
- Prices must have max 2 decimal places
- Category must be one of predefined values
- Specifications must contain at least one property
- All required fields must be present

Error Handling Requirements:
1. CSV Pa