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
 db.books.find();
```
### check existing Indexes
```js
db.books.getIndexes();
```
### check index status before creating
```js
db.books.explain("executionStats").find({ year: { $gt: 1900 } });
```
### create a index 
```js
db.books.createIndex({ year: 1 });
```

### check index status after creating
```js 
db.books.explain("executionStats").find({ year: { $gt: 1900 } });
```

### create compound Indexes
```js
db.books.createIndex({ author: 1, year: -1 });
```

### create unique Indexes
```js
db.books.createIndex({ title: 1 }, { unique: true })
```

### Perform a Basic Text Search
```js
db.books.createIndex({ title: "text", description: "text" });
```

### Search for words
```js
db.books.find({ $text: { $search: "society romantic" } });
```

### call the Indexes
```js
db.books.find({ $text: { $search: "society romantic" } }).pretty()
```
