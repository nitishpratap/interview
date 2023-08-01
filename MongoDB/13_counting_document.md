Sure! Counting documents in MongoDB is a common operation to get the number of documents that match a specific query filter. MongoDB provides several methods for counting documents, each serving different purposes. Below is a complete guide and documentation on how to count documents in MongoDB using various methods.

**1. `countDocuments()` Method:**
The `countDocuments()` method counts the number of documents that match a specified query filter in a collection.

**Syntax:**
```javascript
db.collection.countDocuments(filter, options);
```

**Parameters:**
- `filter`: The query filter that specifies the criteria for counting documents. It uses a BSON document (i.e., a JSON-like object) to define the filter conditions.
- `options` (optional): An optional parameter that can include additional options for the count operation, such as collation and hint.

**Example:**
```javascript
// Count the number of documents in the 'users' collection
const totalCount = db.users.countDocuments();

// Count the number of documents where the 'status' is "active"
const activeCount = db.users.countDocuments({ status: "active" });
```

**2. `estimatedDocumentCount()` Method:**
The `estimatedDocumentCount()` method provides an estimate of the number of documents in a collection without scanning the entire collection. It can be faster than `countDocuments()` for large collections.

**Syntax:**
```javascript
db.collection.estimatedDocumentCount(options);
```

**Parameters:**
- `options` (optional): An optional parameter that can include additional options for the count operation, such as maxTimeMS (maximum execution time).

**Example:**
```javascript
// Get an estimated count of documents in the 'users' collection
const estimatedCount = db.users.estimatedDocumentCount();
```

**3. `count()` Method (Deprecated):**
The `count()` method was deprecated in version 4.0 and replaced by `countDocuments()` or `estimatedDocumentCount()`. It is recommended to use one of the newer methods instead.

**Syntax:**
```javascript
db.collection.count(query);
```

**Parameters:**
- `query`: The query filter that specifies the criteria for counting documents. It uses a BSON document to define the filter conditions.

**Example:**
```javascript
// Deprecated method, use countDocuments() or estimatedDocumentCount() instead
const count = db.users.count({ status: "active" });
```

