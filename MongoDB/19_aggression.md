As of my last update in September 2021, MongoDB Aggregation is a powerful framework that allows you to process and transform data in complex ways within the database. It provides a set of pipeline stages and aggregation operators that enable you to perform data aggregation, grouping, filtering, and other data manipulations. Below is a complete documentation and overview of MongoDB Aggregation:

**Aggregation Pipeline:**
The aggregation pipeline is a sequence of stages that process the documents as they pass through it. Each stage applies a specific operation to the data, and the output of one stage serves as the input to the next stage. The stages can include various aggregation operators, allowing you to perform complex data transformations.

**Aggregation Stages:**
The aggregation pipeline consists of several stages, and you can use multiple stages to build sophisticated data transformation pipelines. Some of the commonly used stages include:
- `$match`: Filters the documents based on specified criteria.
- `$project`: Shapes the output by specifying the fields to include or exclude in the result.
- `$group`: Groups the documents based on a specified key and performs aggregation operations on the grouped data.
- `$sort`: Sorts the documents based on specified fields and sorting orders.
- `$limit`: Limits the number of documents in the output.
- `$skip`: Skips a specified number of documents in the output.
- `$unwind`: Deconstructs an array field and generates a separate document for each element of the array.

**Aggregation Operators:**
Aggregation operators are used within the aggregation pipeline stages to perform various operations on the data. Some of the commonly used aggregation operators include:
- Arithmetic Operators (`$add`, `$subtract`, `$multiply`, `$divide`, etc.): Perform arithmetic operations on numerical values.
- Comparison Operators (`$eq`, `$ne`, `$gt`, `$gte`, `$lt`, `$lte`, etc.): Compare values in documents.
- Array Operators (`$filter`, `$map`, `$reduce`, etc.): Manipulate arrays and their elements in documents.
- Accumulators (`$sum`, `$avg`, `$min`, `$max`, etc.): Perform mathematical operations on grouped data.
- Date Operators (`$dateToString`, `$dayOfMonth`, `$month`, `$year`, etc.): Extract and format date-related information.

**Example Aggregation:**
```javascript
// Example aggregation pipeline to find the average age of users grouped by status
db.users.aggregate([
  { $match: { age: { $exists: true } } },
  { $group: { _id: "$status", avgAge: { $avg: "$age" } } },
  { $sort: { avgAge: -1 } }
]);
```
