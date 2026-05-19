#### Indexing
```js

db.books.insertMany([
  { title: "The Great Gatsby", author: "F. Scott Fitzgerald", year: 1925, genre: "Fiction", description: "A story of wealth and tragedy in the Jazz Age." },
  { title: "To Kill a Mockingbird", author: "Harper Lee", year: 1960, genre: "Fiction", description: "A novel about racism and innocence in the American South." },
  { title: "1984", author: "George Orwell", year: 1949, genre: "Dystopian", description: "A tale of totalitarianism and surveillance in a future society." },
  { title: "Pride and Prejudice", author: "Jane Austen", year: 1813, genre: "Romance", description: "A romantic comedy about manners and marriage." },
  { title: "The Catcher in the Rye", author: "J.D. Salinger", year: 1951, genre: "Fiction", description: "A young boy's rebellion against phony adult world." }
]);
```
### find
```js
// db.books.find();
```
### check existing Indexes
```js
// db.books.getIndexes();
```

// db.books.explain("executionStats").find({ year: { $gt: 1900 } });

db.books.createIndex({ year: 1 });

// db.books.explain("executionStats").find({ year: { $gt: 1900 } });

// create compound Indexes
db.books.createIndex({ author: 1, year: -1 });

// create unique Indexes
db.books.createIndex({ title: 1 }, { unique: true })

// Perform a Basic Text Search
db.books.createIndex({ title: "text", description: "text" });

// Search for words
db.books.find({ $text: { $search: "society romantic" } });


// call the Indexes
db.books.find({ $text: { $search: "society romantic" } }).pretty()
