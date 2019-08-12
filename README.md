# Learning MongoDB

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



## MongoDB Introduction

MongoDB is No-SQL Database. That means non-relational database - which provides a mechanism of storage and retrival of data records that are not modeled on tabular relations, as used in traditional relational databases.

### Why No-SQL, reasons:
- Many new applications require to create huge volumes of new, custom data types which are mix of structured, semi-structured, unstructured and polymorphic data.
- Application development has changed from **Waterfall Model** (which takes long production times - typically 12-18 months) to new rapid faster methods like Agile Sprints, iterating quickly and pushing code every week or two.
- Purpose of applications has now changed from being targeted at some fraction of users to Service that has to be always up and running(very less downtime.. virtually none); globally accessible to millions of users.
- Organizations now use more open software technologies, commodity servers and cloud computing instead of large monolithic servers and storage infrastructures.

> Relational databases were not designed to be capable of such scale and agility challanges, nor are built to take advantage of commodity storage and processing power avaialble today.


## MongoDB Features:
__Note: Ref: https://www.mongodb.com/what-is-mongodb__

- MongoDB **stores data in flexible, JSON-like documents**, meaning fields can vary from document to document and data structure can be changed over time.
- The document model **maps to the objects in your application code**, making data easy to work with.
- **Ad hoc queries, indexing and real time aggregation** provide powerful ways to access and analyze your data.
- MongoDB is a **distributed database at its core**, so high availability, horizontal scaling and geographic distribution are built in and easy to use.
- MongoDB is **free to use**.