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

