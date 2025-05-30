# MongoAssignment2 - Medium
Simple mongodb assignment

### 1 Total Quantity of Products by Supplier
```
db.Assignment2.aggregate([
  {
    $group: {
      _id: "$supplier.name",
      totalQuantity: { $sum: "$quantity" }
    }
  }
]);
```
![1](images/mid/m1.png)
### 2 Average Price of Products per Tag
```
db.Assignment2.aggregate([
{ $unwind: "$tags" },
{
$group: { _id: "$tags", averagePrice: { $avg: "$price" } } },
  { $sort: { averagePrice: -1 } 
}
]);
```
![Screenshot](images/mid/m2.png)
### 3 Products Added in February 2023 (with formatted date)
```
db.Assignment2.aggregate([
  {
    $match: { date_added: { $gte: new Date("2023-02-01"), $lt: new Date("2023-03-01") } }
  },
  {
    $project: {
      name: 1, category: 1,
      formattedDateAdded: { $dateToString: { format: "%Y-%m-%d", date: "$date_added" } }, _id: 0 }
  }
])
```
![Screenshot](images/mid/m3.png)