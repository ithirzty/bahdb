# BahDB
BahDB is a fast relational database, built in [Bah](https://github.com/ithirzty/bah) for Bah.

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

### Conditions
Used for determining which elements must be affected.
```bah
condition = dbWhere("field", DB_EQUALS, value)
//means any element where element.field == value
```

#### Operations
Here is the list of all operations availables:
- `DB_EQUALS`
- `DB_NOT_EQUALS`
- `DB_GREATER`
- `DB_LESS`
- `DB_GREATER_EQUAL`
- `DB_LESS_EQUAL`
- `DB_LIKE`

#### Chaining operations
You can add multiple operations together by using the `+` operator:
```bah
condition = dbWhere("field", DB_EQUALS, value) + dbWhere("field2", DB_LIKE, "%test%")
//means any element where element.field == value
//and element.field2 contains "test"
```

### Setters
Used for updating a specified field of an object.

```bah
setter = dbSet("field", value)
//means any element where element.field = value
```

#### Chaning setters
As operations, setters can be chained using the `+` operator.

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

db.update(condition, template, setter)
```
The template is used as a skeletton, only the fields presents in the template will be kepped.

### Selecting
Used for fetching the requested elements from the databse.
```bah
res = []myStruct*

db.select(condition, res)
```

### Deleting
Used for deleting elements from the database.
```bah
db.delete(condition)
```

## Example
There is an example of the database's usage in the file [test.bah](test.bah).

It is a simple command line interface for registering and managing messages.