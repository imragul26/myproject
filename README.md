How Hashes Look Like in Redis

Redis Hashes store field-value pairs, like a dictionary or map. A single hash key can contain multiple fields, each with an associated value.

Example Data:

Key: user:1001
Fields:  
- name: "John Doe"  
- age: "30"  
- email: "john.doe@example.com"  
- location: "New York"


---

Common Operations on Redis Hashes

1. Adding Data

HSET user:1001 name "John Doe" age "30" email "john.doe@example.com" location "New York"

Adds a hash with fields and values under the key user:1001.


2. Retrieving Data

Get a single field:

HGET user:1001 name
# Output: "John Doe"

Get all fields and values:

HGETALL user:1001
# Output: name "John Doe" age "30" email "john.doe@example.com" location "New York"

Get all field names:

HKEYS user:1001
# Output: ["name", "age", "email", "location"]

Get all values:

HVALS user:1001
# Output: ["John Doe", "30", "john.doe@example.com", "New York"]



3. Updating or Adding New Fields
If the field already exists, it updates the value; otherwise, it adds a new field.

HSET user:1001 age "31"
HSET user:1001 phone "123-456-7890"


4. Deleting Fields

HDEL user:1001 email


5. Checking Field Existence

HEXISTS user:1001 email
# Output: 0 (doesn't exist) or 1 (exists)


6. Incrementing Numeric Fields

HINCRBY user:1001 age 1
# Output: 32




---

Example Use Cases for Hashes

1. User Profiles: Storing user data like name, age, email, and preferences.


2. Configuration Data: Storing application settings in a structured manner.


3. Product Information: Caching product details like name, price, stock, and category.




---

Complex Querying on Redis Hashes

Redis doesn’t support SQL-like queries for hashes. However, you can combine operations and commands to simulate complex queries:

1. Filtering Fields: Use client-side processing to filter results after retrieving the hash. For example, fetch all fields and then filter for a specific condition using your programming language.
