Element operators in MongoDB are used to query and manipulate fields in documents based on their existence, type, and value. They allow you to perform queries that involve checking if a field exists, whether it is of a specific type, or if its value satisfies certain conditions. Below is a complete documentation and guide on how to use element operators in MongoDB:

**1. `$exists` Operator:**
The `$exists` operator checks if a field exists in a document. It returns documents where the specified field is present (regardless of its value) or documents where the field is missing.

**Example:**
```javascript
// Find documents where the 'status' field exists
db.users.find({ status: { $exists: true } });

// Find documents where the 'address' field does not exist
db.users.find({ address: { $exists: false } });
```

**2. `$type` Operator:**
The `$type` operator checks the BSON data type of a field. It returns documents where the specified field has the given data type.

**Example:**
```javascript
// Find documents where the 'age' field is of type "number" (Double or Int32)
db.users.find({ age: { $type: "number" } });

// Find documents where the 'name' field is of type "string"
db.users.find({ name: { $type: "string" } });
```

**3. `$mod` Operator:**
The `$mod` operator performs a modulo operation on the value of a field. It returns documents where the value of the field divided by the specified divisor has the specified remainder.

**Example:**
```javascript
// Find documents where the 'score' field has a remainder of 0 when divided by 5
db.students.find({ score: { $mod: [5, 0] } });
```

**4. `$regex` Operator:**
The `$regex` operator performs a regular expression pattern match on the value of a field. It returns documents where the field's value matches the specified regular expression.

**Example:**
```javascript
// Find documents where the 'email' field contains "example.com"
db.users.find({ email: { $regex: /example\.com/ } });
```

**5. `$text` Operator:**
The `$text` operator performs a full-text search on text fields indexed with a text index. It returns documents that contain the specified search terms.

**Example:**
```javascript
// Find documents that contain the word "mongodb" or "database"
db.articles.find({ $text: { $search: "mongodb database" } });
```

**6. `$where` Operator:**
The `$where` operator allows you to write JavaScript expressions to perform custom queries. It returns documents that satisfy the specified JavaScript expression.

**Example:**
```javascript
// Find documents where the sum of 'field1' and 'field2' is greater than 100
db.collection.find({ $where: function() { return this.field1 + this.field2 > 100; } });
```
