Logical operators in MongoDB are used to perform logical operations in queries, allowing you to combine multiple conditions to create more complex and flexible queries. MongoDB supports various logical operators, including `$and`, `$or`, `$not`, and `$nor`. Below is a complete documentation and guide on how to use logical operators in MongoDB:

**1. `$and` Operator:**
The `$and` operator performs a logical AND operation on an array of two or more conditions, selecting documents that satisfy all the specified conditions.

**Example:**
```javascript
// Find documents where the 'age' is greater than 30 and the 'status' is "active"
db.users.find({ $and: [ { age: { $gt: 30 } }, { status: "active" } ] });
```

**2. `$or` Operator:**
The `$or` operator performs a logical OR operation on an array of two or more conditions, selecting documents that satisfy at least one of the specified conditions.

**Example:**
```javascript
// Find documents where the 'age' is greater than 40 or the 'status' is "inactive"
db.users.find({ $or: [ { age: { $gt: 40 } }, { status: "inactive" } ] });
```

**3. `$not` Operator:**
The `$not` operator performs a logical NOT operation on a single condition, selecting documents that do not satisfy the specified condition.

**Example:**
```javascript
// Find documents where the 'age' is not greater than 30
db.users.find({ age: { $not: { $gt: 30 } } });
```

**4. `$nor` Operator:**
The `$nor` operator performs a logical NOR operation on an array of two or more conditions, selecting documents that do not satisfy any of the specified conditions.

**Example:**
```javascript
// Find documents where the 'age' is not greater than 40 and the 'status' is not "inactive"
db.users.find({ $nor: [ { age: { $gt: 40 } }, { status: "inactive" } ] });
```

**Logical Operators with Other Query Operators:**
Logical operators can be combined with other query operators to create more sophisticated queries. For example, you can use `$and` with other comparison operators to find documents that meet multiple conditions simultaneously.

**Example:**
```javascript
// Find documents where the 'age' is greater than 30 and less than 50
db.users.find({ $and: [ { age: { $gt: 30 } }, { age: { $lt: 50 } } ] });
```
