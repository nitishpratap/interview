Comparison operators in MongoDB are used to compare values within documents and perform various types of comparisons. They allow you to create powerful queries to find documents that satisfy specific conditions based on the values of their fields. Below is a complete guide to the comparison operators in MongoDB:

**1. `$eq` Operator:**
The `$eq` operator checks if the value of a field is equal to the specified value.

**Example:**
```javascript
// Find documents where the 'age' is equal to 30
db.users.find({ age: { $eq: 30 } });
```

**2. `$ne` Operator:**
The `$ne` operator checks if the value of a field is not equal to the specified value.

**Example:**
```javascript
// Find documents where the 'status' is not equal to "inactive"
db.users.find({ status: { $ne: "inactive" } });
```

**3. `$gt` Operator:**
The `$gt` operator checks if the value of a field is greater than the specified value.

**Example:**
```javascript
// Find documents where the 'score' is greater than 80
db.students.find({ score: { $gt: 80 } });
```

**4. `$gte` Operator:**
The `$gte` operator checks if the value of a field is greater than or equal to the specified value.

**Example:**
```javascript
// Find documents where the 'price' is greater than or equal to 100
db.products.find({ price: { $gte: 100 } });
```

**5. `$lt` Operator:**
The `$lt` operator checks if the value of a field is less than the specified value.

**Example:**
```javascript
// Find documents where the 'quantity' is less than 50
db.inventory.find({ quantity: { $lt: 50 } });
```

**6. `$lte` Operator:**
The `$lte` operator checks if the value of a field is less than or equal to the specified value.

**Example:**
```javascript
// Find documents where the 'rating' is less than or equal to 4.5
db.reviews.find({ rating: { $lte: 4.5 } });
```

**7. `$in` Operator:**
The `$in` operator checks if the value of a field matches any of the specified values in an array.

**Example:**
```javascript
// Find documents where the 'color' is either "red" or "blue"
db.products.find({ color: { $in: ["red", "blue"] } });
```

**8. `$nin` Operator:**
The `$nin` operator checks if the value of a field does not match any of the specified values in an array.

**Example:**
```javascript
// Find documents where the 'status' is neither "pending" nor "cancelled"
db.orders.find({ status: { $nin: ["pending", "cancelled"] } });
```
