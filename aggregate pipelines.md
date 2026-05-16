
#### Aggregate operators
#### insert data
```javascript
use shop

db.sales.insertMany([
  { item: "apple", quantity: 5, price: 1 },
  { item: "banana", quantity: 8, price: 0.5 },
  { item: "apple", quantity: 7, price: 1 },
  { item: "orange", quantity: 15, price: 2 },
  { item: "banana", quantity: 4, price: 0.5 },
  { item: "apple", quantity: 3, price: 1 },
  { item: "orange", quantity: 10, price: 2 },
  { item: "grape", tags: ["sweet", "purple"], quantity: 20 }
]);
```

#### 1. `$match`  (like WHERE in SQL)
```javascript
db.sales.aggregate([
  { $match: { quantity: { $gt: 10 } } }  
])
```

#### 2. `$project` - show or create new fields
```javascript
db.sales.aggregate([
  { $project: { item: 1, totalPrice: { $multiply: ["$quantity", "$price"] }, _id: 0 } }
])
```

#### 3. `$group` - (like GROUP BY)
```javascript
db.sales.aggregate([
  { $group: { _id: "$item", totalQty: { $sum: "$quantity" }, avgPrice: { $avg: "$price" } } }
]).
```


#### 4. `$sort` 
```javascript
db.sales.aggregate([
  { $sort: { quantity: -1 } }  
])
```

#### 5. `$limit` 
```javascript
db.sales.aggregate([
  { $limit: 3 }  
])
```

#### 6. `$skip` 
```javascript
db.sales.aggregate([
  { $skip: 2 },  
])
```

#### 7. `$unwind` -makes the entries seprate which contains elements in array.
```javascript
db.sales.aggregate([
  { $match: { item: "grape" } },
  { $unwind: "$tags" }  
])
```

#### 8. `$addFields` 
```javascript
db.sales.aggregate([
  { $addFields: { discount: 10 } } 
])
```

#### 9. `$count`
```javascript
db.sales.aggregate([
  { $match: { quantity: { $gt: 5 } } },
  { $count: "highQuantity" }  
])
```

#### 10. `$lookup` - works like join two another collections and make a single combined report.
First let's create another collection:

```javascript
db.students.insertMany([
  {_id:1,name:'raj',course_id:101},
  {_id:2,name:'sumit',course_id:102}
]);

db.course.insertMany([
  {_id:101,course_name:'python'},
  {_id:102,course_name:'java'}
]);


db.students.aggregate([
  {$lookup:{
    from:'course',
    localField:"course_id",
    foreignField:"_id",
    as:'course_details'}
}])

```

#### 11. `$sortByCount` - Group and count, then sort (shortcut)
```javascript
db.sales.aggregate([
  { $sortByCount: "$item" }  
])
```

#### 12. `$out` - Save results to a new collection
```javascript
db.sales.aggregate([
  { $group: { _id: "$item", total: { $sum: "$quantity" } } },
  { $out: "itemTotals" } 
])
```


#### 13. `$facet` - Run multiple pipelines at once
```javascript
db.sales.aggregate([
  { $facet: {
      "topItems": [ { $sortByCount: "$item" }, { $limit: 2 } ],
      "highQty": [ { $match: { quantity: { $gt: 10 } } }, { $count: "count" } ]
    }
  }
])
  
  
```
