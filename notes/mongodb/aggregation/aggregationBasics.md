## MongoDB aggregation

The aggregation pipeline **is a framework** for data aggregation modeled on the concept of data processing pipelines. Documents enter a multi-stage pipeline that transforms the documents into aggregated results

You can group matched documents. You can name the fields, perform sum and other operations. Example

> MongoDB provides the db.collection.aggregate() method

```js
db.orders.aggregate([
   { $match: { status: "A" } },
   { $group: { _id: "$cust_id", total: { $sum: "$amount" } } }
])
```

- First stage: The `$match` stage filters the documents by the ***status*** field and passes to the next stage
- Second stage: The `$group` stage groups the documents by the ***cust_id*** field to calculate the sum of the amount for each unique ***cust_id***

#### Pipeline
The MongoDB aggregation pipeline consists of stages. Each stage transforms the documents as they pass through the pipeline. Pipeline stages do not need to produce one output document for every input document; e.g., some stages may generate new documents or filter out documents.

[Aggregation Pipeline Stages](https://docs.mongodb.com/manual/reference/operator/aggregation-pipeline/#aggregation-pipeline-operator-reference)

### Article no 1 [link](https://www.compose.com/articles/aggregations-in-mongodb-by-example/)


> Aggregations are a set of functions that allow you to manipulate the data being returned from a MongoDB query

> The **aggregate** function accepts an array of data transformations which are applied to the data **in the order** they're defined

### Article no 2 [link](https://studio3t.com/knowledge-base/articles/mongodb-aggregation-framework/)

The `$match()` stage filters those documents we need to work with, those that fit our needs.

> Stage approach allows us to check whether our query is functioning properly at every stage by examining both its input and the output. The output of each stage will be the input of the next.

Aggregation query example:
```js
pipeline = [
  { $match : { … },
  { $group : { … },
  { $sort : { … },
  ...
]
db.collectionName.aggregate(pipeline, options)
```

Up to 100 MB of RAM can be used per stage.
Solution: enable the disk instead of RAM:
`db.collectionName.aggregate(pipeline, { allowDiskUse : true })`

Aggregation stages:
1. `$match`
   Filters the documends. Same as .find({...})
1. `$project`
   Allows to pick the fields from the document. Same as .find({}, {...})
1. `$group`
   We can perform summary queries such as finding `count`, `totals`, `averages`...
1. `$unwind`
   This stage enables us to work with the values of the fields within an array
   In other words, it unwraps particular array field into duplicated documents with only difference - unwinded field!!!
1. `$sort`
   Sorts the documents in a pipeline
   _Query example below:_
   ```js
      db.universities.aggregate([
   { $match : { name : 'USAL' } },
   { $unwind : '$students' },
   { $project : { _id : 0, 'students.year' : 1, 'students.number' : 1 } },
   { $sort : { 'students.number' : -1 } }
   ]).pretty()
   ```
1. `$limit` limit the results to 2 ex. `{ $limit : 2 }`
1. `$addFields` ex. `{ $addFields : { foundation_year : 1218 } }` add new field
1. `$count` 
1. `$lookup` help you to join 2 collections on a field [Mongo Lookup Docs](https://docs.mongodb.com/manual/reference/operator/aggregation/lookup/)
   ```js
   { $lookup : {
      from : 'foreign collection name',
      localField : 'field to replace',
      foreignField : 'foreign collection field to use for join',
      as : 'new name for localField'
   }}
   ```
1. `$sortByCount` sort by the count of occurences for `level` `{ $sortByCount : '$level' }`
1. `$facet` running multi pipelines at a time
   ```js
   { $facet : {
      "pipeline1": [{...}],
      "pipeline2": [{...}]
   }
   // Returns
   {
      "pipeline1": [{/*pipeline1 result*/}, {}]
      "pipeline2": [{/*pipeline2 result*/}, {}]
   }
   ```

> **You can use Mongo Compass to track each stage output**