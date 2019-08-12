# MongoDB with Python:

### Install the Python Driver (PyMongo)

There are multiple Mongo Drivers for python, but I prefer to use PyMongo - as it is the official Python Driver for PyMongo.

```python
pip install pymongo
```
or
```python
python -m pip install pymongo
```

Example of using this in Python Code:

```python
from pymongo import MongoClient

client = MongoClient('mongodb://%s:%s@127.0.0.1:3129' %(username, password))
```

### Further Details:
| Topic | Link |
| --- | --- |
|Authentication|[Details]()|
