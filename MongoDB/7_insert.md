In MongoDB, the `insert()` method is used to insert one or more documents into a collection. However, as of MongoDB version 3.2, the `insert()` method is deprecated, and you should use `insertOne()` or `insertMany()` for single and multiple document insertions, respectively. Below is a complete documentation and guide on how to use `insertOne()` and `insertMany()` methods in MongoDB:

**1. `insertOne()` Method:**
The `insertOne()` method inserts a single document into a collection. It takes a single document as an argument and returns a result object that includes information about the insertion operation.

**Syntax:**
```javascript
db.collection.insertOne(document, options);
```

**Parameters:**
- `document`: The document to be inserted into the collection. It must be a valid BSON document (i.e., a JSON-like object).
- `options` (optional): An optional parameter that can include additional options for the insertion operation, such as write concern and bypass document validation.

**Example:**
```javascript
db.users.insertOne({
  "name": "John Doe",
  "age": 30,
  "email": "john@example.com"
});
```

**2. `insertMany()` Method:**
The `insertMany()` method inserts multiple documents into a collection. It takes an array of documents as an argument and returns a result object that includes information about the insertion operation.

**Syntax:**
```javascript
db.collection.insertMany(documents, options);
```

**Parameters:**
- `documents`: An array of documents to be inserted into the collection. Each element in the array must be a valid BSON document.
- `options` (optional): An optional parameter that can include additional options for the insertion operation, such as write concern and bypass document validation.

**Example:**
```javascript
db.products.insertMany([
  { "name": "Product 1", "price": 20.99 },
  { "name": "Product 2", "price": 15.50 },
  { "name": "Product 3", "price": 10.00 }
]);
```

**Result Object:**
Both `insertOne()` and `insertMany()` methods return a result object with the following properties:
- `acknowledged`: A boolean indicating if the operation was acknowledged by the MongoDB server.
- `insertedId`: The _id of the inserted document(s). For `insertOne()`, it will be the _id of the single inserted document. For `insertMany()`, it will be an array of _ids for the multiple inserted documents.

**Error Handling:**
If an error occurs during the insertion operation, MongoDB will throw an exception. You should handle potential errors appropriately, especially when inserting multiple documents, as some documents may be inserted successfully while others may fail.
