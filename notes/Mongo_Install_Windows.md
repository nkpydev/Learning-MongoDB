## Installation on Local Windows 10 Machine

1. Download MongoDB Server (Community) 4.0

- [MongoDB Download](https://www.mongodb.com/download-center/community) ".msi version"

2. Run Installation

3. Basic Logic:

-   2 IMP .exe's that are available are:
    - mongo.exe [This is actual MongoDB server]
    - mongod.exe [This is event listener]

-   _Data Storage_:
    - Create a directory "data" in:
        -  C:\ *or* C:\Program Files\MongoDB
    - inside that "data" directory create one more named "db"
    - So, this "C:\data\db" or "C:\Program Files\MongoDB\data\db" is the local storage where all your database files will be stored.

- _Access_:
    - Default when you install on local machine, the localhost (127.0.0.1) is the bindIp for MongoDB
    - If you want the MongoDB Server on you local host to be accessed from remote machine, you will have to do some configuration changes on both:
        - your local machine firewall settings
            - Run this on PowerShell:
            ```shell
            New-NetFirewallRule `
            -DisplayName "Allow MongoDB" `
            -Direction Inbound `
            -Protocol TCP `
            -LocalPort 27017 `
            -Action Allow
            ```
        - your MongoDB listener (mongod.exe) settings, rather change in "mongod.conf" file:
            ```cmd
            net:
                port: 27017
                bindIp: [127.0.0.1,10.0.0.4,x.x.x.x,..]
            ```
            
## Initial Work

### Activating the "mongod"

Once you have installed MongoDB on your local machine, go to Command Prompt and write:
```shell
mongod
```
By running this command, you are actually executing, "mongod.exe", who activates "Mongo Daemon", which is basically the host process for database. Kind of event listener.

### Activating the "mongo"

This is executing "mongo.exe", which is an instance of the "Mongo Database" from the Daemon.
```shell
mongo
```

### Creating the User Authentication on MongoDB

Once you sure that both above commands are working properly, exit them both and start a "command prompt" (cmd)

```shell
mongo
.
.
.
(Some Log and Basic instance info)
.
.

> use admin
switched to db admin

```
_Note:_ If the database "admin" is not present, MongoDB will automatically create one.

Here once you are into admin database, you need to create user Administrator

| Attribute | Value |
| --- | --- |
| database | admin |
| privilege | userAdminAnyDatabase |
| user | myUserAdmin (any name you want) |
| pwd | (yourSecretPassword) |  
| roles | [{role: privilege, db: database}]


```python
db.createUser(
    {
        user: "myUserAdmin",
        pwd: "abc123",
        roles: [
            {
                role: "userAdminAnyDatabase",
                db: "admin"
            }
        ]
    }
)

> 
```
This should create your userAdminstrator.

Again close all instances of MongoDB and reopen command-prompt (cmd), to write:

```shell
mongod --port 27017 -u "myUserAdmin" -p "abc123" --authenticationDatabase "admin"
```

_Note_: userAdministrator user has only permission to create and manage the database users, you cannot read, write using this user. MongoDB will throw an error on trying this.


### Create normal Read/Write Users

First lets create a new Database - "testdb"

```shell
use testdb
```

Then create an user for this Database - "normalUser"

```python
db.createuser(
    {
        user: "normalUser",
        pwd: "abc#123",
        roles: [
            {
                role: "readWrite",
                db: "testdb"
            }
        ]
    }
)
```

Now we can login using this user in MongoURI, like this:

```python

from pymongo import MongoClient

URI = "mongodb://normalUser:abc#123@127.0.0.1:27017/testdb"
client = MongoClient(URI)
db = client.testdb
```