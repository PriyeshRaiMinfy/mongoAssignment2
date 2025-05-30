# MongoAssignment2 - Easy
Simple mongodb assignment

### 1 All products in the "Electronics" category
```
db.Assignment2.aggregate([
  { $match: { category: "Electronics" } }
]);

```
![1](images/easy/e1.png)
### 2 Count products per category
```
db.Assignment2.aggregate([
  { $group: { _id: "$category", count: { $sum: 1 } } }
]);

```
![Screenshot](images/easy/e2.png)
### 3 Product names and prices, sorted by price descending
```
db.Assignment2.aggregate([
  { $project: { _id: 0, name: 1, price: 1 } },
  { $sort: { price: -1 } }
]);

```
![Screenshot](images/easy/e3.png)