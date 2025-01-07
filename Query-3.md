# MongoDB CRUD Operations and Exercises

## 1. Additional Questions on CRUD Operations:

### Insert new students into the "students" collection with random data.
```json
db.students.insertMany([
    { "name": "John Doe", "roll_number": "001", "department": "CS", "courses": ["CS101", "MATH101"], "year": 2023 },
    { "name": "Jane Smith", "roll_number": "002", "department": "EE", "courses": ["EE101", "PHYS101"], "year": 2023 },
    { "name": "Alice Johnson", "roll_number": "003", "department": "ME", "courses": ["ME101", "CHEM101"], "year": 2023 }
])
```

### Update the department of a student based on their roll number.
```json
db.students.updateOne(
    { "roll_number": "001" },
    { $set: { "department": "IT" } }
)
```

### Remove all students who have enrolled in less than 3 courses.
```json
db.students.deleteMany(
    { "courses": { $size: { $lt: 3 } } }
)
```

## 2. Aggregation Exercise:

### Use aggregation to find the department with the most number of students.
```json
db.students.aggregate([
    { $group: { _id: "$department", count: { $sum: 1 } } },
    { $sort: { count: -1 } },
    { $limit: 1 }
])
```

## 3. Advanced Querying Exercise:

### Query students who have enrolled in a specific set of courses (e.g., CS101 and MATH101).
```json
db.students.find(
    { "courses": { $all: ["CS101", "MATH101"] } }
)
```

## 4. Indexing and Performance:

### Experiment with creating indexes on various fields like department, year, etc., and measure the query performance using explain().
```json
db.students.createIndex({ "department": 1 })
db.students.createIndex({ "year": 1 })

db.students.find({ "department": "CS" }).explain("executionStats")
db.students.find({ "year": 2023 }).explain("executionStats")
```