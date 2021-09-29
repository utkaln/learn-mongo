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
