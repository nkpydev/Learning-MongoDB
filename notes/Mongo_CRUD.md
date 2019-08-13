# CRUD - what is that?
- **C**reate
- **R**ead
- **U**pdate
- **D**elete

Basic set of operations on any Database are - Create, Read, Update and Delete; more easily denoted as CRUD Operations.

### Basic Query examples in SQL vs. MongoDB:

| SQL | MongoDB |
|---|---|
|select * from Table_Name | db.collection.find({})|
|select * from Table_Name where status = "D"| db.collection.find{'status':'D'}|
|select * from Table_Name where status in ("A","D")| db.collection.find({'status': {"$in":['A','D']}})|
|select * from Table_Name where status = "A" and qty < 30 | db.collection.find({'status':'A','qty' : {"$lt" :30}})|


### Connect to MongoDB and view a list of available Databases

```python
from pymongo import MongoClient
URI = 'mongodb://127.0.0.1:27017'
client = MongoClient()