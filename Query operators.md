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
