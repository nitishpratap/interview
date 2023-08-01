Sure! Below is a complete guide and documentation on various MongoDB delete methods, including `deleteOne()`, `deleteMany()`, and `remove()`.

**1. `deleteOne()` Method:**
The `deleteOne()` method deletes a single document from a collection that matches a specified filter. It removes the first document that matches the criteria.

**Syntax:**
```javascript
db.collection.deleteOne(filter, options);
```

**Parameters:**
- `filter`: The query filter that specifies the criteria for selecting the document to delete. It uses a BSON document (i.e., a JSON-like object) to define the filter conditions.
- `options` (optional): An optional parameter that can include additional options for the delete operation, such as write concern.

**Example:**
```javascript
// Delete the first document where the 'name' is "John Doe"
db.users.deleteOne({ name: "John Doe" });
```

**2. `deleteMany()` Method:**
The `deleteMany()` method deletes multiple documents from a collection that match a specified filter. It removes all documents that meet the criteria.

**Syntax:**
```javascript
db.collection.deleteMany(filter, options);
```

**Parameters:**
- `filter`: The query filter that specifies the criteria for selecting the documents to delete. It uses a BSON document to define the filter conditions.
- `options` (optional): An optional parameter that can include additional options for the delete operation, such as write concern.

**Example:**
```javascript
// Delete all documents where the 'status' is "inactive"
db.users.deleteMany({ status: "inactive" });
```

**3. `remove()` Method (Deprecated):**
The `remove()` method was deprecated in version 4.0 and replaced by the more specific `deleteOne()` and `deleteMany()` methods. It is recommended to use `deleteOne()` or `deleteMany()` instead of `remove()`.

**Syntax:**
```javascript
db.collection.remove(query, justOne);
```

**Parameters:**
- `query`: The query filter that specifies the criteria for selecting the document(s) to remove. It uses a BSON document to define the filter conditions.
- `justOne` (optional): A boolean parameter that specifies whether to delete only one document (true) or all matching documents (false).

**Example:**
```javascript
// Delete the first document where the 'name' is "John Doe"
db.users.remove({ name: "John Doe" }, true); // Equivalent to deleteOne()

// Delete all documents where the 'status' is "inactive"
db.users.remove({ status: "inactive" }, false); // Equivalent to deleteMany()
```
