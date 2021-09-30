# learn-mongo

## Getting Started

### Commands
```mongo
// Connection (To mongo atlast free tier) using mongosh
mongosh "mongodb+srv://cluster0.lsnlm.mongodb.net/myFirstDatabase" --username <username>

// Check available database names
// shows local db that mongo uses for internal purpose
show dbs 

// shows myFirstDatabase as the name where user can enter data
db

// Switch to another db
use secondDB

// save data (document) to a collection
db.myFirstDB.insertOne({_id: 1, value:'hello world !'})

// read data that was saved to collection
db.myFirstDB.find()

```

## Advantages of Mongo DB
* Fully managed
* Reliable
* Performance
* Global
* Productivity
* Secure
* Easy to migrate between different cloud providers, or move to in prem
* Primary and secondary nodes can be between different providers too
* Optimize performance by creating or dropping recommended indexes. Also recommends improve schemas


### Mapping between RDBMS and Mongo
* Database --> Database
* Table --> Collection
* Parent-Child Table --> Nested sub document
* Index --> Index
* Row --> Document
* Column --> Field
* Join --> $looku, Linking, Embedding
* View --> view
* ACID Trx --> ACID Trx

#### $jsonSchema Operator
* This operator matches document that satisfy the JSON schema


#### Sharding
* provides efficiency over hardware limitation by distributing data
* Range Based - Driven by date
* Hash based - Distributing uniformly based on when they were entered, so they are unlikely to be in the same shard if they were entered immediately after one another
* Tag based / Zone based - User specific config drives what shard to go to

## Useful queries

```mongo
// insert()
db.mytab.insert(
  {item: "envelope", qty: 100, type: "something"}
)

// find()
db.mytab.find({x:1, y:2}, {a:1, b:1, c:1})

// findOne() - returns the first occurrence

// update()
db.mytab.update(
  {author: "Tom"},
  {$set: {author: "Thomas"}},
  {multi: true}
)

// remove()
db.mytab.remove({qty: { $gt: 20}}, true)

// variations of find 
find({genres: {$in:["Comedy", "Drama"]}})

find({revenues: {$exists: true}})

// Starts with the character pattern
({title: {$regex: '^Dr. Strangelove'}})

```

### Aggregation Queries
* Aggregation queries function better because it is simplistic like unix - Match --> Group --> Sort

```mongo
db.orders.aggregate(
  {$match: {status: "A"}},
    {$group: { _id: "$cust_id", total: {$sum: "$amount"}}
)
```

### Tips for Mongo Compass
* Select table and go to Explain Plan that shows query performance
* Create index to improve, in the example we chose - cast, title, year all in ascending order
* Aggregation queries can be easily done in compass using aggregation pipeline
*   $match, 
* Custom Aggregation: $match --> $project --> $group --> $merge
* Add Data is an easy way to add 

### Data Modeling in Mongo
* High level steps: Develop the application, Define the data model then go in cycles of improving application and improving data model
* The application design drives the data model
* Understand read/ write usage, keep in mind about whether read more or write more

#### Link vs. Embed
* Relationship - Choice to connect one document to another
* **Embed** One to One, One to many, many to many

### Design Patterns
* **Bucket Pattern** - Rapid transactions instead of being individual document, can be merged to one doc while writing to better index
* **Computed Pattern** - Good for more reads. Reduce reads by capturing calculated data. Example: while writing just calculate and keep it. Compute on write is less work than compute on read. 
* **Caching Pattern** - Good for read heavy

### Patterns for many to many
* use $unwind to make multiple objects to individual document, then group or aggregate how you want

### Using Mongo Compass

#### Filters
```mongo

```

