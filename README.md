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
                binfIp: [127.0.0.1,10.0.0.4,x.x.x.x,..]
            ```



## MongoDB Introduction

