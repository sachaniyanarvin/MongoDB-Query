# Task 1: Create a "CodingGita Students" database

## Create Database and Collections

```mongodb
use CodingGita

db.createCollection("students")
db.createCollection("courses")
```

## Insert Sample Data

### Insert Students

```mongodb
db.students.insertMany([
    { name: "John Doe", roll_number: "CS001", department: "Computer Science", year: 2, courses_enrolled: ["CS101", "CS102"] },
    { name: "Jane Smith", roll_number: "ME001", department: "Mechanical Engineering", year: 1, courses_enrolled: ["ME101", "ME102"] }
])
```

### Insert Courses

```mongodb
db.courses.insertMany([
    { course_code: "CS101", name: "Introduction to Computer Science", credits: 3, instructor: "Dr. Alan Turing" },
    { course_code: "CS102", name: "Data Structures", credits: 4, instructor: "Dr. Grace Hopper" },
    { course_code: "ME101", name: "Thermodynamics", credits: 3, instructor: "Dr. James Watt" },
    { course_code: "ME102", name: "Fluid Mechanics", credits: 4, instructor: "Dr. Blaise Pascal" }
])
```

# Task 2: Perform CRUD operations

## Add More Students and Courses

### Add Students

```mongodb
db.students.insertMany([
    { name: "Alice Johnson", roll_number: "CS002", department: "Computer Science", year: 3, courses_enrolled: ["CS101", "CS103"] },
    { name: "Bob Brown", roll_number: "EE001", department: "Electrical Engineering", year: 2, courses_enrolled: ["EE101", "EE102"] }
])
```

### Add Courses

```mongodb
db.courses.insertMany([
    { course_code: "CS103", name: "Algorithms", credits: 4, instructor: "Dr. Donald Knuth" },
    { course_code: "EE101", name: "Circuit Analysis", credits: 3, instructor: "Dr. Nikola Tesla" },
    { course_code: "EE102", name: "Electromagnetics", credits: 4, instructor: "Dr. Michael Faraday" }
])
```

## Query Data

### Query by Department

```mongodb
db.students.find({ department: "Computer Science" })
```

### Query by Year

```mongodb
db.students.find({ year: 2 })
```

### Query by Courses Enrolled

```mongodb
db.students.find({ courses_enrolled: "CS101" })
```

## Update Courses for a Specific Student

```mongodb
db.students.updateOne(
    { roll_number: "CS001" },
    { $addToSet: { courses_enrolled: "CS103" } }
)
```

## Delete a Student or Course

### Delete a Student

```mongodb
db.students.deleteOne({ roll_number: "ME001" })
```

### Delete a Course

```mongodb
db.courses.deleteOne({ course_code: "ME101" })
```