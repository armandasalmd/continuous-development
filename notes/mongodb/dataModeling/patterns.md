## Data modeling patterns

Patterns are the most powerful tool for designing schemas for MongoDB/NoSql

Patters - reuseable units of knowledge

### ![sky blue](https://placehold.it/15/10fabc/000000?text=+)  Handling duplication, staleness, referential integrity
#### Duplication

Why? | Concern?
------------ | -------------
Result of embedding info in a given doc for faster access (no joins) | Data inconsistency, correctness

Duplication choice depends on situation

#### Staleness

Why? | Concern?
------------ | -------------
New events come along in a big rate | Data quality, reliability (many data was not updated?)

Example: We have a list of weekly salaries and we want to get a sum of it. Instead of storying it, we might calculate it on spot when needed

#### Referential integrity

Why? | Concern?
------------ | -------------
No support for document cascading (reference deletion) | Data inconsistency, correctness
Linking info between documents or tables | -

Example: We have a list of weekly salaries and we want to get a sum of it. Instead of storying it, we might calculate it on spot when needed

### ![sky blue](https://placehold.it/15/10fabc/000000?text=+)  Patterns

- Attribute pattern
- Extended Reference pattern
- Subset pattern
- Computer pattern
- Bucket pattern
- Schema Versioning pattern
- Tree patterns
- Polymorphic pattern
