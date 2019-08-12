## MongoDB Concepts:

| RelationalDB Concept | MongoDB Equivalent |
| --- | --- |
| Database | Database |
| Tables | Collections |
| Rows | Documents |
| Index | Index |

### Example of Document:
```python
{
    first_name: 'Paul',     #String
    last_name: 'Miller',    #String
    cell: 44123456789,      #Number
    city: 'London',
    location: [45.123, 47.232],     #Geo-Coordinates
    profession: ['banking','finance','trader'],     #Fields can contain Arrays
    cars: [ 
        {   model: 'Bentley',       #Fields can contain an array of sub-documents
            year: 1973,
            value: 10000
        }
        {
            model: 'Rolls Royce',
            year: 1965,
            value: 33000
        }
    ]

}
```


### MongoDB - Compass:

The GUI for MongoDB, to visually explore your data.

![MongoDB - Compass](/assets/MongoDB_Compass.jpg)

You can view the Databases and their Collections thr' the Compass GUI.

![MongoDB - Compass Connected](/assets/MongoDB_Compass_Connected.jpg)

View of Document inside a Collection thr' Compass.

![MongoDB - Compass Document inside the Collection](/assets/MongoDB_Compass_Collection_Document.jpg)