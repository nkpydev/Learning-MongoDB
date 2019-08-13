## MongoDB Authentication:

MongoDB supports several different authentication mechanisms.

### Percent-Escaping Username and Password

username and password must be precent-escaped with urllib.parse.quote_plus()

Example:
```python
from pymongo import MongoClient
import urllib.parse

username = urllib.parser.quote_plus('user')
password = urllib.parse.quote_plus('password')
client = MongoClient('mongodb://%s:%s@127.0.0.1' %(username, password))
```

### SCRAM-SHA-256 (RFC 7677)

SCRAM-SHA-256 is the default mechanism supported by a cluster configured for authentication with MongoDB 4.0 or later.
Authentication requires a username, a password, and a database name. The default database name is “admin”, this can be overidden with the authSource option. 

Example:
```python
from pymongo import MongoClient
client = MongoClient('exmaple.com',
                        username = 'user',
                        password = 'password',
                        authSource = 'the_database',
                        authMechanism = 'SCRAM-SHA-256'
                    )
```
or the MongoDB URI method:

```python
uri = "mongodb://user:password@example.com/?authSource=the_database&authMechanism=SCRAM-SHA-256"
client = MongoClient(uri)
```
