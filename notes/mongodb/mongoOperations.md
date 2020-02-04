## MongoDB CRUD Operations

> CRUD operations create, read, update, and delete documents

### ![purple](https://placehold.it/15/e9b6b3/000000?text=+) Create (insert into a collection)

If the collection does not currently exist, insert operations will create the collection.

-   db.collection.insert()
-   db.collection.insertOne()
-   db.collection.insertMany()

```js
db.collection('inventory').insertOne({
	item: 'canvas',
	qty: 100,
	tags: ['cotton'],
	size: { h: 28, w: 35.5, uom: 'cm' }
})
```

### ![purple](https://placehold.it/15/e9b6b3/000000?text=+) Query

##### Select all elements in a Collection

_`db.inventory.find( {} )`_

##### Equality condition

Syntax `{ <field1>: <value1>, ... }`
_`db.inventory.find( { status: "D" } )`_

##### Conditions Using Query Operators

Syntax `{ <field1>: { <operator1>: <value1> }, ... }`
_`db.inventory.find( { status: { $in: [ "A", "D" ] } } )`_ return status equal either "A" or "D"

##### Specify AND as well as OR Conditions

example

```js
db.inventory.find({
	status: 'A',
	$or: [{ qty: { $lt: 30 } }, { item: /^p/ }]
})
```

##### Nested selection

Use . to select a child
`db.inventory.find( { "size.uom": "cm" } )`
`db.inventory.find( { "size.h": { $lt: 15 } } )`
and
`db.inventory.find( { "size.h": { $lt: 15 }, "size.uom": "in", status: "D" } )`

##### Matching with an array

OR logic
`db.inventory.find( { tags: ["red", "blank"] } )`
`db.inventory.find( { dim_cm: { $gt: 15, $lt: 20 } } )`
AND logic
`db.inventory.find( { tags: { $all: ["red", "blank"] } } )`
Query an Array by Array Length (colors are stored in array)
`db.inventory.find( { "tags": { $size: 3 } } )`

##### Selecting from array where exactly object match

`db.inventory.find( { "instock": { $elemMatch: { qty: 5, warehouse: "A" } } } )`

##### Select what fields to return

Use second parameter, \_id field by default is 1(on)
`db.inventory.find( { status: "A" }, { item: 1, status: 1 } )`

##### Return All But the Excluded Fields

All fields are on, you just exclude some (by setting 0)
`db.inventory.find( { status: "A" }, { status: 0, instock: 0 } )`

##### Multilevel document selection example

```
db.inventory.find({ status: 'A' }, { item: 1, status: 1, 'size.uom': 1 });
```

##### Existance check

Match where do not contain the item field
`db.inventory.find( { item : { $exists: false } } )`

##### Iterator index

```js
var myCursor = db.inventory.find({ type: 2 })
var documentArray = myCursor.toArray() // !!!!! with some drivers
var myDocument = documentArray[3]
```

### ![purple](https://placehold.it/15/e9b6b3/000000?text=+) Update

Update field operators

-   \$currentDate - sets to current date
-   \$inc - increments by given amount
-   \$min/max - only updates if given value is less/greater than existing
-   \$mul - multiplies the field by given value
-   \$rename - rename a field
-   \$set - set value
-   \$unset - removes field from the document

Array operators

-   \$addToSet - adds element if not exists in an array
-   \$pop - removes first/last item of an array
-   \$pull - removes all array elements that match
-   \$push - adds
-   \$pullAll - removes all matching values from an array

Modifiers

-   $each - modifies $push and \$addToSet to append multiple items
-   $position - modifies $push
-   $slice - modifies $push to limit the size of updated elements
-   $sort - modifies $push

Example:

```js
{
  _id: 1,
  sku: "abc123",
  quantity: 10,
  metrics: {
    orders: 2,
    ratings: 3.5
  },
},
//
db.products.update(
   { sku: "abc123" },
   { $inc: { quantity: -2, "metrics.orders": 1 } },
)
// RESULT
{
   "_id" : 1,
   "sku" : "abc123",
   "quantity" : 8,
   "metrics" : {
      "orders" : 3,
      "ratings" : 3.5
   },
},
```

Pushing to array example:

```js
// Single value
db.students.update({ _id: 1 }, { $push: { scores: 89 } })
// Multiple values
db.students.update(
	{ name: 'joe' },
	{ $push: { scores: { $each: [90, 92, 85] } } }
)
```
