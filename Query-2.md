```markdown
### Task 1: Add multiple students
```json
db.students.insertMany([
    { rollNumber: 1, name: "Alice", department: "Computer Science", year: 2, subjects: ["NodeJS", "React"] },
    { rollNumber: 2, name: "Bob", department: "Electrical Engineering", year: 1, subjects: ["C++", "Mathematics"] },
    { rollNumber: 3, name: "Charlie", department: "Mechanical Engineering", year: 3, subjects: ["Thermodynamics", "Mechanics"] },
    { rollNumber: 4, name: "David", department: "Computer Science", year: 2, subjects: ["NodeJS", "MongoDB"] },
    { rollNumber: 5, name: "Eve", department: "Civil Engineering", year: 4, subjects: ["Structures", "Fluid Mechanics"] }
]);
```

### Task 2: Add multiple subjects
```json
db.subjects.insertMany([
    { name: "NodeJS", topics: ["Express", "Middleware", "Routing"] },
    { name: "React", topics: ["Components", "State", "Props"] },
    { name: "MongoDB", topics: ["CRUD", "Aggregation", "Indexing"] },
    { name: "C++", topics: ["OOP", "STL", "Pointers"] }
]);
```

### Task 3: Query students based on subject enrollment
```json
db.students.find({ subjects: "NodeJS" });
```

### Task 4: Add a new topic to a subject
```json
db.subjects.updateOne(
    { name: "NodeJS" },
    { $push: { topics: "Async Programming" } }
);
```

### Task 5: Query subjects with multiple topics
```json
db.subjects.find({ topics: { $size: { $gte: 4 } } });
```

### Task 6: Update student enrollment
```json
db.students.updateOne(
    { name: "Jenil" },
    { $push: { subjects: "React Native" } }
);
```

### Task 7: Query all students
```json
db.students.find({}, { name: 1, subjects: 1 });
```

### Task 8: Update multiple students' year
```json
db.students.updateMany(
    { department: "Computer Science" },
    { $set: { year: 3 } }
);
```

### Task 9: Add new topics to multiple subjects
```json
db.subjects.updateOne(
    { name: "React" },
    { $push: { topics: "Hooks" } }
);
db.subjects.updateOne(
    { name: "NodeJS" },
    { $push: { topics: "Event Loop" } }
);
db.subjects.updateOne(
    { name: "MongoDB" },
    { $push: { topics: "Replication" } }
);
```

### Task 10: Remove a topic from a subject
```json
db.subjects.updateOne(
    { name: "NodeJS" },
    { $pull: { topics: "Express" } }
);
```

### Task 11: Query all students in a specific year
```json
db.students.find({ year: { $in: [2, 3] } });
```

### Task 12: Delete a student by roll number
```json
db.students.deleteOne({ rollNumber: 3 });
```

### Task 13: Delete all students from a department
```json
db.students.deleteMany({ department: "Electrical Engineering" });
```

### Task 14: Retrieve all topics for a subject
```json
db.subjects.find({ name: "MongoDB" }, { topics: 1 });
```

### Task 15: Count the number of subjects in which a student is enrolled
```json
db.students.aggregate([
    { $project: { name: 1, numberOfSubjects: { $size: "$subjects" } } }
]);
```