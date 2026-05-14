## Date 12 May 2026

```yml
// updateOne 
db.students.updateOne(
    { name:"Alice" },
    { $set : { age: 21 }, $push : { hobbies : "Swimming" }}
    
);
//updateMany
db.students.updateMany(
  { status : "active" },
  { $inc : { gpa :- 0.1 }}
) ;  

// replaceOne 
db.students.replaceOne(
    { name : "Alice" },
    { name : "Alice" ,age: 34 , major: "Design ", gpa : 3.7 }
);







-- Operator	Use Case
--  $set	Add or update fields
-- $unset	Remove fields
-- $inc	Increase or decrease values
-- $mul	Multiply values
-- $rename	Rename fields
-- $min	Store minimum value
-- $max	Store maximum value
-- $currentDate	Store current date/time





db.employees.insertMany([
  {
    _id: 1,
    name: "Amit",
    department: "IT",
    salary: 40000,
    experience: 2,
    rating: 3
  },
  {
    _id: 2,
    name: "Neha",
    department: "HR",
    salary: 35000,
    experience: 3,
    rating: 4
  },
  {
    _id: 3,
    name: "Rahul",
    department: "Finance",
    salary: 50000,
    experience: 5,
    rating: 5
  },
  {
    _id: 4,
    name: "Priya",
    department: "Sales",
    salary: 32000,
    experience: 1,
    rating: 2
  },
  {
    _id: 5,
    name: "Karan",
    department: "IT",
    salary: 60000,
    experience: 7,
    rating: 5
  }
]);





// Check Records
// db.employees.find().limit(10)

// $set - update operator 
db.employees.updateOne(
  { _id: 1 },
  { $set: { department: "Sales", location: "Surat" } }
);



// $unset() - remove

db.employees.updateOne(
  { _id: 1 },
  { $unset: { rating: 1 } }
);



// $inc()
db.employees.updateOne(
  { _id: 1 },
  { $inc: { salary: 5000 } }
);


db.employees.find({_id:1});

// $mul()

db.employees.updateOne(
  { _id: 1 },
  { $mul: { experience: 2 } }
)

db.employees.find({_id:1});

// $rename 
db.employees.updateOne(
  { _id: 1 },
  { $rename: { experience: "totalExperience" } }
);

db.employees.find({_id:1});

// $min -> Salary becomes 42000 because 42000 < 45000.

db.employees.updateOne(
  { _id: 1 },
  { $min: { salary: 42000 } }
);

db.employees.find({_id:1});


// $max

db.employees.updateOne(
  { _id: 1 },
  { $max: { salary: 60000 } }
)


db.employees.find({_id:1});

// $currentDate

db.employees.updateOne(
  { _id: 1 },
  { $currentDate: { lastUpdated: true } }
)


db.employees.find({_id:1});


```
