# BahDB
BahDB is a fast relational database, built in Bah for Bah.

It is really simple to use and really shows how simple and elegant Bah can be.

## Features
- [x] thread safe
- [x] process safe
- [x] scanning
- [x] serializing
- [x] indexing
- [x] portable

## Documentation
The database interface.

### Declaring a database
```bah
db = bahDB{}
```

### Opening/closing a file
Used for mapping the database to a file.
```bah
db.open("path/to/my/database.db")

//database stuff

db.close()
```

### Inserting
Used for inserting an element in the database.
```bah
myElem = new myStruct
db.insert(myElem)
```

### Updating
Used for updating the content of an element inside the database.
```bah
template = new myStruct

db.update("field", value, template, "fielToSet", valueToSet)
```

### Selecting
Used for fetching the requested elements from the databse.
```bah
res = []myStruct*

db.select("field", value, res)
```

### Deleting
Used for deleting elements from the database.
```bah
db.delete("field", value)
```

## Example
There is an example of the database's usage in the file [test.bah](test.bah).

It is a simple command line interface for registering and managing messages.