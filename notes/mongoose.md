## Mongoose

[Find documentation here](https://mongoosejs.com/docs/guide.html)

### Getting started

1st, MongoDB and Node.js installed
2nd, `$ npm i mongoose`
3rd, connect

```js
// getting-started.js
var mongoose = require('mongoose');
mongoose.connect('mongodb://localhost/test', { useNewUrlParser: true });
```

4th, bind listeners

```js
var db = mongoose.connection;
db.on('error', console.error.bind(console, 'connection error:'));
db.once('open', function() {
	// we're connected!
});
```

5th, define **schema**

```js
var kittySchema = new mongoose.Schema({
	name: String
});
```

6th, **compile**/add the schema

```js
var Kitten = mongoose.model('Kitten', kittySchema);
```

7th, **create** model **instance**

```js
var silence = new Kitten({ name: 'Silence' });
console.log(silence.name); // 'Silence'
```

8th, adding custom **functions** to model

```js
// NOTE: methods must be added to the schema before compiling it with mongoose.model()
kittySchema.methods.speak = function() {
	var greeting = this.name
		? 'Meow name is ' + this.name
		: "I don't have a name";
	console.log(greeting);
};

var Kitten = mongoose.model('Kitten', kittySchema);

// using that methond example
var fluffy = new Kitten({ name: 'fluffy' });
fluffy.speak(); // "Meow name is fluffy"
```

9th, **saving** model instance to mongo

```js
fluffy.save(function(err, fluffy) {
	if (err) return console.error(err);
	fluffy.speak();
});
```

10th, **finding all** saved instances

```js
Kitten.find(function(err, kittens) {
	if (err) return console.error(err);
	console.log(kittens);
});
```

11th, **finding with filter** instances

```js
Kitten.find({ name: /^fluff/ }, callback);
```

### Schemas

1st, defining your schema

> Schema - defines the shape of the documents within that collection

```js
var mongoose = require('mongoose');
var Schema = mongoose.Schema;

var blogSchema = new Schema({
	title: String, // String is shorthand for {type: String}
	author: String,
	body: String,
	comments: [{ body: String, date: Date }],
	date: { type: Date, default: Date.now },
	hidden: Boolean,
	meta: {
		votes: Number,
		favs: Number
	}
});
```

2nd, schema types

-   String
-   Number
-   Date
-   Buffer
-   Boolean
-   Mixed
-   ObjectId
-   Array
-   Decimal128
-   Map

**_Schema_** is only a definition **_Model_** is an instance of schema we can work with. `var Blog = mongoose.model('Blog', blogSchema);`

> **Instances of Models are documents!**

##### Statics (model functions)

```js
// Assign a function to the "statics" object of our animalSchema
animalSchema.statics.findByName = function(name) {
	return this.find({ name: new RegExp(name, 'i') });
};
// Or, equivalently, you can call `animalSchema.static()`.
animalSchema.static('findByBreed', function(breed) {
	return this.find({ breed });
});

const Animal = mongoose.model('Animal', animalSchema);
let animals = await Animal.findByName('fido');
animls = animals.concat(await Animal.findByBreed('Poodle'));
```

> Do not declare statics using ES6 arrow functions (=>)

##### Indexes

> With mongoose, we define these indexes within our Schema

```js
var animalSchema = new Schema({
	name: String,
	type: String,
	tags: { type: [String], index: true } // field level
});

animalSchema.index({ name: 1, type: -1 }); // schema level
```

##### Virtuals

Instead of

```js
console.log(axl.name.first + ' ' + axl.name.last); // Axl Rose
```

Use virtual

```js
personSchema.virtual('fullName').get(function() {
	return this.name.first + ' ' + this.name.last;
});
console.log(axl.fullName); // Axl Rose
```

To set fullname

```js
personSchema
	.virtual('fullName')
	.get(function() {
		return this.name.first + ' ' + this.name.last;
	})
	.set(function(v) {
		this.name.first = v.substr(0, v.indexOf(' '));
		this.name.last = v.substr(v.indexOf(' ') + 1);
	});

axl.fullName = 'William Rose'; // Now `axl.name.first` is "William"
```

### SchemaType

> A SchemaType is then a configuration object for an individual property. A SchemaType says what type a given path should have

Example

```js
// 3 string SchemaTypes: 'name', 'nested.firstName', 'nested.lastName'
const schema = new Schema({
	name: { type: String },
	nested: {
		firstName: { type: String },
		lastName: { type: String }
	}
});
```

All schema types

-   `required`: boolean or a function<boolean>
-   `default`: default value
-   `select`: boolean, specifies default projections for queries
-   `validate`: validation function
-   `get`: custom getter
-   `set`: custom setter
-   `index`: boolean
-   `unique`: boolean
-   `lower/uppercase`: boolean, do always convert the string
-   `trim`: boolean, trim the string
-   `match`: RedExp, creates a _validator_
-   `enum`: array, create a _validator_ to check if value matches array
-   `min/maxlength`: number, creates validator that checks...
-   `min/max`: number, checks the integer if valid

### Models

> An instance of a model is called a document.

```js
var schema = new mongoose.Schema({ name: 'string', size: 'string' });
var Tank = mongoose.model('Tank', schema);
```

1st param is a name of collection to create a document in and then schema

On the model we can perform these commands:

-   Save **.save**(errorHandlerFunction)
-   Query **.find()**.where().gt().exec(callback)
-   Delete **.deleteOne**(query, errorHandlerFunction)
-   Updating **.updateOne**(query, replaceQuery, errorHandlerFunction)

Update example

```js
doc.name = 'foo';

// Mongoose sends a `updateOne({ _id: doc._id }, { $set: { name: 'foo' } })`
// to MongoDB.
await doc.save();
```

### Queries

> Mongoose models provide several static helper functions for CRUD operations

##### Executing

params: query, selected fields, callback

```js
var Person = mongoose.model('Person', yourSchema);

// find each person with a last name matching 'Ghost', selecting the `name` and `occupation` fields
Person.findOne({ 'name.last': 'Ghost' }, 'name occupation', function(
	err,
	person
) {
	if (err) return handleError(err);
	// Prints "Space Ghost is a talk show host".
	console.log(
		'%s %s is a %s.',
		person.name.first,
		person.name.last,
		person.occupation
	);
});
```

exmaple

```js
// With a JSON doc
Person.find({
	occupation: /host/,
	'name.last': 'Ghost',
	age: { $gt: 17, $lt: 66 },
	likes: { $in: ['vaporizing', 'talking'] }
})
	.limit(10)
	.sort({ occupation: -1 })
	.select({ name: 1, occupation: 1 })
	.exec(callback);

// Using query builder
Person.find({ occupation: /host/ })
	.where('name.last')
	.equals('Ghost')
	.where('age')
	.gt(17)
	.lt(66)
	.where('likes')
	.in(['vaporizing', 'talking'])
	.limit(10)
	.sort('-occupation')
	.select('name occupation')
	.exec(callback);
```

### Validation for testing

```js
var schema = new Schema({
	name: {
		type: String,
		required: true
	}
});
var Cat = db.model('Cat', schema);

// This cat has no name :(
var cat = new Cat();
cat.save(function(error) {
	assert.equal(error.errors['name'].message, 'Path `name` is required.');

	error = cat.validateSync();
	assert.equal(error.errors['name'].message, 'Path `name` is required.');
});
```
