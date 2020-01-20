## Data modeling patterns

Patterns are the most powerful tool for designing schemas for MongoDB/NoSql

Patters - reuseable units of knowledge

### ![sky blue](https://placehold.it/15/10fabc/000000?text=+) Handling duplication, staleness, referential integrity

#### Duplication

| Why?                                                                 | Concern?                        |
| -------------------------------------------------------------------- | ------------------------------- |
| Result of embedding info in a given doc for faster access (no joins) | Data inconsistency, correctness |

Duplication choice depends on situation

#### Staleness

| Why?                                | Concern?                                               |
| ----------------------------------- | ------------------------------------------------------ |
| New events come along in a big rate | Data quality, reliability (many data was not updated?) |

Example: We have a list of weekly salaries and we want to get a sum of it. Instead of storying it, we might calculate it on spot when needed

#### Referential integrity

| Why?                                                   | Concern?                        |
| ------------------------------------------------------ | ------------------------------- |
| No support for document cascading (reference deletion) | Data inconsistency, correctness |
| Linking info between documents or tables               | -                               |

Example: We have a list of weekly salaries and we want to get a sum of it. Instead of storying it, we might calculate it on spot when needed

### ![sky blue](https://placehold.it/15/10fabc/000000?text=+) Patterns

-   Attribute pattern
-   Extended Reference pattern
-   Subset pattern
-   Computer pattern
-   Bucket pattern
-   Schema Versioning pattern
-   Tree patterns
-   Polymorphic pattern

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Attribute pattern

It helps to organize fields that have either common characteristics you want to search across, or fields that are rare

It potentially reduces the number of indexes.

To use it, transpose the key/values of the desired properties into an array of documents.

Example:

```js
{
	"brand": "MongoDB",
	"price": 0.0,
	...
	"input": "5V/1300 mA",
	"output": "5V/1A",
	"capacity": "4200 mAh"
}
// transforms to
{
	"brand": "MongoDB",
	"price": 0.0,
	...
	"specs": [
		{ "k": "input", "v": "5V/1300 mA"},
		{ "k": "output", "v": "5V/1A"},
		{ "k": "capacity", "v": 4200, "unit": "mAh" }
	]
}
```

| Problem                           | Solution                                                         |
| --------------------------------- | ---------------------------------------------------------------- |
| Lots of similar fields            | Break the field/value into an array with object key/value        |
| Want to search across many fields | {"color": "blue, "size": "large"}                                |
| -                                 | { [ {"k": "color", "v": "blue"}, {"k": "size", "v": "large"} ] } |

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Extended Reference pattern

Pattern often used in catalogs, mobile applications, and real-time analytics.

Copy the fields you want to access frequently

Works best if you do not change the fields often

Be careful when updating source (customers address) - update extended references

![](https://i.gyazo.com/fc14a9ccab4c919612b4c4016efcdf8e.png)

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Subset pattern

Proble occurs when working set is to big
![](https://i.gyazo.com/e55cb2c7d42a82b6fe8d58269e69d0bd.png)

Fix by:

-   Add RAM
-   Scale with Sharding
-   Reduce the size on the working set **(subset pattern)**

How to do it?: Take large documents and decide which information is important and which is extra. Split them to a different collections.

> Example: **movies** collection is to big. create **movies_extra** and put less relevant info there associating by any reference

![](https://i.gyazo.com/207d08fad50d9eced0339c162459754b.png)

_movies_extra_ can be accessed by the `$lookup` operator

| Problem                                   | Solution                                  |
| ----------------------------------------- | ----------------------------------------- |
| Working set is to big                     | Split into 2 collections                  |
| A lot of pages are evicted from memory    | 1st. most used into, 2nd. least used info |
| Large part of documents are rarely needed | -                                         |

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Computed pattern

Sometimes we access the document a lot of times and it usually returns similar results after calculation. This gets expensive when user base groups and we calculate same outputs. **Goal**. Reduce computation

![](https://i.gyazo.com/e6da43a3ec2cea96f5d8d093546320ee.png)

**In this example it is better to calc total revenue and store it in the root rather then calculating the sum all over again on request**

An example of roll-up. Store calculated values elsewhere

![](https://i.gyazo.com/5da8542bd1271bab043fcc2bb8575703.png)

When to apply:

-   Overused CPU
-   Reduce latency for read operations

| Problem                | Solution                                 |
| ---------------------- | ---------------------------------------- |
| Avoid same computation | Perform calculation and store the result |

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Bucket pattern

Problem occurs when data is constantly being added.
What we do is store data in buckets (array in this example); It is a good idea to split pressure, temp, light buckets into different collections if we need to access them 1 at the time.

> Remember that mongo db brings documents to the memory and multiple buckets in document can be an issue!

![](https://i.gyazo.com/6d583d27dafec4b539f2dbc336d5b105.png)

| Problem                                                | Solution                                                                       |
| ------------------------------------------------------ | ------------------------------------------------------------------------------ |
| Avoid too many documents, instead bucket them in 1 doc | Define constant amount of data to be grouped together (like temp for 24 hours) |
| one-to-many relation cannot be embedded                | Create arrays to store info in main object                                     |

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Schema Versioning pattern

Sometimes the shape of the document changes. How to minimize the downtime? Implement Schema Versioning!

You can create different db handlers to response according to `schema version`

![](https://i.gyazo.com/3416aad2343308b1ea9740a9bc38189b.png)

| Problem                            | Solution                                  |
| ---------------------------------- | ----------------------------------------- |
| Avoid downtime while upgrading db  | Each document gets "schema_version" field |
| Upgrading documents can take hours | App can handle all schema versions        |

> Caution. Make your database migratable!!! You are in charge of data

> **Used when app is in production and is heavily used**

##### ![sky blue](https://placehold.it/15/b3ffb3/000000?text=+) Tree patterns

Model tree structures

-   Parent references
-   Child references
-   Array of Ancestors
-   Materialized Paths
-   MongoMart solution: Array of Ancestors and Parent references

[Tutorial from mongodb team](https://university.mongodb.com/mercury/M320/2020_January_7/chapter/Chapter_4_Patterns_Part_2_/lesson/5ccaf964a668ca660cd49f2a/lecture)

#### Approximation pattern

is used if many request are made but the number in db dont have to be precise. Like youtube views. You can store 10 views up in app and then add 10 views for db record.

#### Outlier pattern

is used when a document stores many objects in an array, like subscribers. Solution: add `number_of_subscribers` and `has_overflow_subscribers` where overflow is stored in different document
