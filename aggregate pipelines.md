
#### Aggregate operators
#### insert data
```javascript

db.students.insertMany([
  {
    name: "Alice",
    age: 20,
    major: "Computer Science",
    gpa: 3.8,
    graduationYear: 2024,
    address: { city: "New York", zip: "10001" },
    status: "active",
    hobbies: ["Reading", "Coding"]
  },
  {
    name: "Bob",
    age: 22,
    major: "Biology",
    gpa: 3.5,
    graduationYear: 2023,
    address: { city: "Boston", zip: "02101" },
    status: "inactive",
    hobbies: ["Sports"]
  },
  {
    name: "Charlie",
    age: 19,
    major: "Math",
    gpa: 4,
    address: { city: "Chicago" },
    status: "active",
    hobbies: ["Music"]
  },
  {
    name: "Diana",
    age: 21,
    major: "Physics",
    gpa: 3.9,
    graduationYear: 2025,
    address: { city: "LA", zip: "90001" },
    status: "active",
    hobbies: ["Gaming", "Reading"]
  },
  {
    name: "Eve",
    age: 23,
    major: "Computer Science",
    gpa: null,
    graduationYear: 2026,
    address: { city: "Seattle", zip: "98101" },
    status: "probation"
  }
])
//unwind makes the entries seprate which contains elements in array.

// db.students.aggregate([
//   { $match: { name: "Diana" } },
//   { $unwind: "$hobbies" }
// ]).pretty()

// addfields 
// db.students.aggregate([
//   { $addFields: { course: "full stack" } }  
// ]);

// count 
// db.students.aggregate([
//   { $match: { graduationYear:{$lte: 2026} }},
//   { $count: "batch 2026" } ]);
  
  
  
// lookup works like join two another collections and make a single combined report.
// db.students.insertMany([
//   {_id:1,name:'raj',course_id:101},
//   {_id:2,name:'sumit',course_id:102}
// ]);

// db.course.insertMany([
//   {_id:101,course_name:'python'},
//   {_id:102,course_name:'java'}
// ]);


// db.students.aggregate([
//   {$lookup:{
//     from:'course',
//     localField:"course_id",
//     foreignField:"_id",
//     as:'course_details'}
// }]);

// sortbycount
db.students.aggregate([
  { $sortByCount: "$name" }  
]);

```
