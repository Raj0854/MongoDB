## insert random data
```js
db.students.drop()

const majors = [
  "Computer Science", "Biology", "Math", "Physics",
  "Chemistry", "Statistics", "Electronics", "Mechanical",
  "Civil", "AI & ML"
]

const cities = [
  "New York", "Boston", "Chicago", "Seattle",
  "San Francisco", "Los Angeles", "Houston",
  "Dallas", "Miami", "Denver"
]

const hobbiesList = [
  "coding", "gaming", "reading", "hiking",
  "painting", "music", "sports", "chess",
  "traveling", "photography", "blogging"
]

const statuses = ["active", "inactive", "probation"]

const names = [
  "Alice", "Bob", "Charlie", "Diana", "Eve", "Frank",
  "Grace", "Henry", "Isabella", "Jack", "Kevin", "Lily",
  "Mike", "Nina", "Oscar", "Paul", "Queen", "Ryan",
  "Sophia", "Tom", "Uma", "Victor", "Will", "Xavier",
  "Yash", "Zara"
]

let students = []

for (let i = 1; i <= 120; i++) {

  // Random hobbies
  let hobbies = []
  let hobbyCount = Math.floor(Math.random() * 4)

  for (let j = 0; j < hobbyCount; j++) {
    hobbies.push(
      hobbiesList[Math.floor(Math.random() * hobbiesList.length)]
    )
  }

  // Remove duplicate hobbies
  hobbies = [...new Set(hobbies)]

  // Random scores
  let scores = []
  let scoreCount = Math.floor(Math.random() * 5) + 1

  for (let k = 0; k < scoreCount; k++) {
    scores.push(Math.floor(Math.random() * 41) + 60) // 60 - 100
  }

  students.push({
    name: names[Math.floor(Math.random() * names.length)] + "_" + i,
    age: Math.floor(Math.random() * 8) + 18, // 18 - 25
    major: majors[Math.floor(Math.random() * majors.length)],
    gpa: Math.random() > 0.1
      ? Number((Math.random() * 2 + 2).toFixed(1)) // 2.0 - 4.0
      : null,

    enrolled: Math.random() > 0.2,

    hobbies: hobbies,

    address: {
      city: cities[Math.floor(Math.random() * cities.length)],
      zip: Math.random() > 0.2
        ? String(Math.floor(Math.random() * 90000) + 10000)
        : null
    },

    scores: scores,

    graduationYear: Math.random() > 0.15
      ? Math.floor(Math.random() * 3) + 2024
      : null,

    status: statuses[Math.floor(Math.random() * statuses.length)]
  })
}

db.students.insertMany(students)


db.students.find()
```
```javascript
// $eq 
db.students.find({ age: { $eq: 21 } });
```

```javascript
// $ne – Not equal
db.students.find({ major: { $ne: "Computer Science" } });
```

```javascript
// $gt – Greater than
db.students.find({ gpa: { $gt: 3.7 } });
```

```javascript
// $gte 
db.students.find({ age: { $gte: 22 } });
```

```javascript
// $lt 
db.students.find({ age: { $lt: 20 } });
```

```javascript
// $lte 
db.students.find({ gpa: { $lte: 3.5 } });
```

```javascript
// $in – value in the list
db.students.find({ name: { $in: ["Alice", "Eve"] } });
```

```javascript
// $nin- not in
db.students.find({ status: { $nin: ["active"] } });
```



```javascript
// $and 
db.students.find({ $and: [{ enrolled: true }, { age: { $gt: 20 } }] });
```

```javascript
// $or
db.students.find({ $or: [{ major: "Math" }, { gpa: 4.0 }] });
```

```javascript
// $not
db.students.find({ age: { $not: { $lt: 21 } } });
```

```javascript
// $nor
db.students.find({ $nor: [{ major: "Physics" }, { major: "Math" }] });
```



```javascript
// $exists: true 
db.students.find({ "address.zip": { $exists: true } });

```

```javascript
// $exists: false 
db.students.find({ "address.zip": { $exists: false } });
```

```javascript
// $type 
db.students.find({ gpa: { $type: "null" } });
```


```javascript
// Exact array match
db.students.find({ hobbies: ["coding", "gaming"] });

```

```javascript
// $all
db.students.find({ hobbies: { $all: ["gaming", "painting"] } });
```

```javascript
// $size 
db.students.find({ scores: { $size: 3 } });
```

```javascript
// $elemMatch 
db.students.find({ scores: { $elemMatch: { $gte: 95, $lte: 100 } } });
```


```javascript
db.students.find({ enrolled: true }, { name: 1, gpa: 1, _id: 0 });
```

```javascript
db.students.find({}, { scores: 0, hobbies: 0 });

```

```javascript
// $slice 
db.students.find({}, { name: 1, scores: { $slice: 2 }, _id: 0 });

```

```javascript
// $elemMatch in projection – Return only matching array elements
db.students.find(
  { hobbies: "gaming" },
  { name: 1, hobbies: { $elemMatch: { $eq: "gaming" } }, _id: 0 }
).pretty()
// Shows only ["gaming"] in hobbies for Alice and Diana
```

```javascript
// Nested field projection
db.students.find({}, { "address.city": 1, _id: 0 }).pretty()
// Shows only the city inside address
```
