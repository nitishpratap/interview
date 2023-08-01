In MongoDB, the `update()` method was deprecated in version 3.2 and replaced by more specific update methods, `updateOne()` and `updateMany()`. These methods are used to update one or multiple documents in a collection that match a specified filter or criteria. Below is a complete guide and documentation on how to use `updateOne()` and `updateMany()` methods in MongoDB:

**1. `updateOne()` Method:**
The `updateOne()` method updates a single document in a collection that matches a specified filter. It takes two arguments: the filter to select the document to update and the update operation to apply.

**Syntax:**
```javascript
db.collection.updateOne(filter, update, options);
```

**Parameters:**
- `filter`: The query filter that specifies the criteria for selecting the document to update. It uses a BSON document (i.e., a JSON-like object) to define the filter conditions.
- `update`: The update operation to apply to the selected document. It uses a BSON document to specify the changes to be made.
- `options` (optional): An optional parameter that can include additional options for the update operation, such as upsert (insert if document not found) and write concern.

**Example:**
```javascript
// Update the 'age' field to 35 for the document where the 'name' is "John Doe"
db.users.updateOne({ name: "John Doe" }, { $set: { age: 35 } });
```

**2. `updateMany()` Method:**
The `updateMany()` method updates multiple documents in a collection that match a specified filter. It takes two arguments: the filter to select the documents to update and the update operation to apply.

**Syntax:**
```javascript
db.collection.updateMany(filter, update, options);
```

**Parameters:**
- `filter`: The query filter that specifies the criteria for selecting the documents to update. It uses a BSON document to define the filter conditions.
- `update`: The update operation to apply to the selected documents. It uses a BSON document to specify the changes to be made.
- `options` (optional): An optional parameter that can include additional options for the update operation, such as upsert and write concern.

**Example:**
```javascript
// Update the 'status' field to "inactive" for all documents where the 'age' is greater than 40
db.users.updateMany({ age: { $gt: 40 } }, { $set: { status: "inactive" } });
```

**3. Update Operators:**
In the update operation, you use update operators to modify specific fields or elements within a document. MongoDB provides various update operators, such as `$set`, `$unset`, `$inc`, `$push`, `$pull`, and many more.

**Example:**
```javascript
// Use $inc operator to increment the 'count' field by 1 for the document with 'name' as "Product A"
db.products.updateOne({ name: "Product A" }, { $inc: { count: 1 } });
```
