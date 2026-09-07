# MongoDB Basics

## Starting MongoDB from Command Prompt

**Installation guidelines:** https://youtu.be/ibAR4n0SjJA?si=hNTsEBWYptNOYo_4
<br/>
**MongoDB Theory:** https://www.geeksforgeeks.org/mongodb/mongodb-an-introduction/


After installing **MongoDB Community Server** and **MongoDB Shell (`mongosh`)**, open **Command Prompt (CMD)**.

Start MongoDB Shell using:

```text
mongosh
```

After the connection is established, a MongoDB prompt will appear. MongoDB commands can now be entered directly.

> **Note:** Older material may show the command `mongo`. Current MongoDB installations use `mongosh`.

To exit MongoDB Shell:

```javascript
exit
```

---

## What is MongoDB?

**MongoDB** is a **NoSQL document-oriented database**.

Unlike a relational database where information is stored in **tables, rows, and columns**, MongoDB stores information as **documents** inside **collections**.

### Relational Database vs MongoDB

| Relational Database | MongoDB |
| --- | --- |
| Database | Database |
| Table | Collection |
| Row | Document |
| Column | Field |
| Primary Key | `_id` |

For example, in an RDBMS, a student might be represented as a row:

```text
RollNo | Name  | Course       | Semester
101    | Aarav | MSc. CA & IT | 1
```

In MongoDB, the same data is represented as a document:

```javascript
{
    rollNo: 101,
    name: "Aarav",
    course: "MSc. CA & IT",
    semester: 1
}
```

MongoDB documents use a **JSON-like structure**. Internally, MongoDB stores documents in **BSON (Binary JSON)** format.

---

## Important MongoDB Terms

### Database

A **database** contains collections.

Example:

```text
collegeDB
```

### Collection

A **collection** contains related documents.

Example:

```text
students
```

Conceptually:

```text
collegeDB
    |
    └── students
          |
          ├── Student Document 1
          ├── Student Document 2
          └── Student Document 3
```

### Document

A **document** stores data in the form of **field-value pairs**.

```javascript
{
    name: "Aarav",
    age: 22,
    course: "MSc. CA & IT"
}
```

Here:

```text
name       → Field
"Aarav"    → Value

age        → Field
22         → Value
```

---

## The `_id` Field and ObjectId

Every MongoDB document must contain a unique field named **`_id`**.

The `_id` field works similarly to a **Primary Key** in a relational database because its value uniquely identifies a document.

If an `_id` is not supplied while inserting a document, MongoDB automatically generates one.

Example:

```javascript
{
    _id: ObjectId("68b4c1a21a23456789abcdef"),
    rollNo: 101,
    name: "Aarav"
}
```

By default, the automatically generated `_id` value has the BSON data type **ObjectId**.

An ObjectId is a **12-byte BSON value**, normally displayed as a **24-character hexadecimal string**.

> **Important:** `_id` itself is a field. Its value is commonly of type `ObjectId`, but MongoDB also allows other unique values such as numbers or strings to be used as `_id`.

For example, an `_id` can be manually provided:

```javascript
db.students.insertOne({
    _id: 101,
    name: "Aarav",
    course: "MSc. CA & IT"
})
```

The `_id` value must be **unique within the collection**.

### Find a Document Using `_id`

Suppose MongoDB generated:

```text
ObjectId("68b4c1a21a23456789abcdef")
```

The document can be found uniquely using:

```javascript
db.students.findOne({
    _id: ObjectId("68b4c1a21a23456789abcdef")
})
```

If a numeric `_id` was manually provided:

```javascript
db.students.findOne({
    _id: 101
})
```

Since `_id` is unique, searching by `_id` identifies at most one document.

---

# Basic MongoDB Commands

## Show Existing Databases

```javascript
show dbs
```

This displays the available databases.

---

## Create / Switch a Database

```javascript
use collegeDB
```

This command switches to the `collegeDB` database.

> **Note:** If the database does not exist, MongoDB creates it when some data is stored in it.

Check the currently selected database:

```javascript
db
```

---

## Create a Collection

Create a collection named `students`:

```javascript
db.createCollection("students")
```

Display the collections in the current database:

```javascript
show collections
```

> **Note:** MongoDB can automatically create a collection when the first document is inserted into it.

---

# CRUD Operations

**CRUD** stands for:

| Operation | Meaning | MongoDB Operation |
| --- | --- | --- |
| **C** | Create | Insert |
| **R** | Read | Find |
| **U** | Update | Update |
| **D** | Delete | Delete |

---

# INSERT – Add Documents

## Insert One Document

`insertOne()` inserts one document into a collection.

```javascript
db.students.insertOne({
    rollNo: 101,
    name: "Aarav",
    course: "MSc. CA & IT",
    semester: 1,
    marks: 78
})
```

MongoDB automatically adds `_id` if it is not provided.

---

## Insert Multiple Documents

`insertMany()` inserts multiple documents.

```javascript
db.students.insertMany([
    {
        rollNo: 102,
        name: "Diya",
        course: "MSc. CA & IT",
        semester: 1,
        marks: 85
    },
    {
        rollNo: 103,
        name: "Kabir",
        course: "MSc. CA & IT",
        semester: 1,
        marks: 69
    },
    {
        rollNo: 104,
        name: "Meera",
        course: "MSc. CA & IT",
        semester: 1,
        marks: 91
    }
])
```

---

# READ – Retrieve Documents

## Display All Documents

```javascript
db.students.find()
```

In an RDBMS, the basic idea is similar to:

```sql
SELECT * FROM students;
```

---

## Find One Document

`findOne()` returns one matching document.

```javascript
db.students.findOne({
    rollNo: 102
})
```

---

## Find Documents Using a Field

```javascript
db.students.find({
    name: "Diya"
})
```

---

# Comparison Query Operators

Comparison operators are used to filter documents according to conditions.

| Operator | Meaning |
| --- | --- |
| `$eq` | Equal to |
| `$ne` | Not equal to |
| `$gt` | Greater than |
| `$gte` | Greater than or equal to |
| `$lt` | Less than |
| `$lte` | Less than or equal to |
| `$in` | Matches any value in a given list |
| `$nin` | Does not match values in a given list |

## `$eq` – Equal To

Find students having exactly `85` marks:

```javascript
db.students.find({
    marks: { $eq: 85 }
})
```

A simpler equivalent is:

```javascript
db.students.find({
    marks: 85
})
```

---

## `$ne` – Not Equal To

Find students whose marks are not `85`:

```javascript
db.students.find({
    marks: { $ne: 85 }
})
```

---

## `$gt` – Greater Than

Find students having marks greater than `80`:

```javascript
db.students.find({
    marks: { $gt: 80 }
})
```

---

## `$gte` – Greater Than or Equal To

Find students having marks greater than or equal to `80`:

```javascript
db.students.find({
    marks: { $gte: 80 }
})
```

---

## `$lt` – Less Than

Find students having marks less than `80`:

```javascript
db.students.find({
    marks: { $lt: 80 }
})
```

---

## `$lte` – Less Than or Equal To

Find students having marks less than or equal to `78`:

```javascript
db.students.find({
    marks: { $lte: 78 }
})
```

---

## `$in` – Match Any Value from a List

Find students whose marks are either `78`, `85`, or `91`:

```javascript
db.students.find({
    marks: { $in: [78, 85, 91] }
})
```

Another useful example:

```javascript
db.students.find({
    name: { $in: ["Aarav", "Diya"] }
})
```

---

## `$nin` – Not in a List

Find students whose marks are not `69` or `78`:

```javascript
db.students.find({
    marks: { $nin: [69, 78] }
})
```

---

# Multiple Conditions

## Implicit AND

When multiple conditions are written in the same query, MongoDB treats them as **AND** conditions.

Find students whose semester is `1` and marks are greater than `80`:

```javascript
db.students.find({
    semester: 1,
    marks: { $gt: 80 }
})
```

---

## `$and` Operator

The same condition can be written explicitly using `$and`:

```javascript
db.students.find({
    $and: [
        { semester: 1 },
        { marks: { $gt: 80 } }
    ]
})
```

---

## `$or` Operator

Find students whose marks are less than `70` OR greater than `90`:

```javascript
db.students.find({
    $or: [
        { marks: { $lt: 70 } },
        { marks: { $gt: 90 } }
    ]
})
```

---

# UPDATE – Modify Documents

## `updateOne()`

Change the marks of roll number `103` to `75`:

```javascript
db.students.updateOne(
    { rollNo: 103 },
    { $set: { marks: 75 } }
)
```

The first part:

```javascript
{ rollNo: 103 }
```

specifies **which document should be updated**.

The second part:

```javascript
{ $set: { marks: 75 } }
```

specifies **what should be changed**.

---

## Update Using `_id`

A document can also be updated uniquely using its `_id`:

```javascript
db.students.updateOne(
    { _id: ObjectId("68b4c1a21a23456789abcdef") },
    { $set: { marks: 88 } }
)
```

---

## `updateMany()`

Update multiple matching documents:

```javascript
db.students.updateMany(
    { semester: 1 },
    { $set: { status: "Active" } }
)
```

---

## `$inc` – Increment a Numeric Value

Increase the marks of roll number `101` by `2`:

```javascript
db.students.updateOne(
    { rollNo: 101 },
    { $inc: { marks: 2 } }
)

Note: like $inc exists, there is no $dec exists!
```

---

# DELETE – Remove Documents

## `deleteOne()`

Delete the student having roll number `104`:

```javascript
db.students.deleteOne({
    rollNo: 104
})
```

---

## Delete Using `_id`

```javascript
db.students.deleteOne({
    _id: ObjectId("68b4c1a21a23456789abcdef")
})
```

Using `_id` is useful when the exact document to delete is known.

---

## `deleteMany()`

Delete all students having marks less than `40`:

```javascript
db.students.deleteMany({
    marks: { $lt: 40 }
})
```

---

# Useful Query Methods

These methods are especially useful after learning basic CRUD operations.

## `countDocuments()`

Count all documents:

```javascript
db.students.countDocuments()
```

Count students having marks greater than or equal to `80`:

```javascript
db.students.countDocuments({
    marks: { $gte: 80 }
})
```

---

## `sort()`

Sort students by marks in ascending order:

```javascript
db.students.find().sort({
    marks: 1
})
```

Sort in descending order:

```javascript
db.students.find().sort({
    marks: -1
})
```

| Value | Sorting |
| --- | --- |
| `1` | Ascending |
| `-1` | Descending |

---

## `limit()`

Display only the first two documents:

```javascript
db.students.find().limit(2)
```

---

## Projection

Projection is used to select which fields should appear in the result.

Display only `name` and `marks`:

(1 is **inclusion projection**)

```javascript
db.students.find(
    {},
    { name: 1, marks: 1 }
)
```

MongoDB includes `_id` by default. To hide it:

```javascript
db.students.find(
    {},
    { _id: 0, name: 1, marks: 1 }
)
```

---

# Drop a Collection

To completely delete the `students` collection:

```javascript
db.students.drop()
```

> **Warning:** This deletes the collection and all documents stored inside it.

---

# Drop a Database

To delete the currently selected database:

```javascript
db.dropDatabase()
```

> **Warning:** This deletes the entire current database along with its collections and documents.


---

# Command summary:

```javascript
mongosh

show dbs

use databaseName

db

db.createCollection("collectionName")

show collections

db.collectionName.insertOne({...})

db.collectionName.insertMany([
    {...},
    {...}
])

db.collectionName.find()

db.collectionName.findOne({ field: value })

db.collectionName.find({
    _id: ObjectId("OBJECT_ID_HERE")
})

db.collectionName.find({
    field: { $eq: value }
})

db.collectionName.find({
    field: { $ne: value }
})

db.collectionName.find({
    field: { $gt: value }
})

db.collectionName.find({
    field: { $gte: value }
})

db.collectionName.find({
    field: { $lt: value }
})

db.collectionName.find({
    field: { $lte: value }
})

db.collectionName.find({
    field: { $in: [value1, value2] }
})

db.collectionName.find({
    field: { $nin: [value1, value2] }
})

db.collectionName.find({
    $or: [
        { condition1 },
        { condition2 }
    ]
})

db.collectionName.updateOne(
    { condition },
    { $set: { field: value } }
)

db.collectionName.updateMany(
    { condition },
    { $set: { field: value } }
)

db.collectionName.deleteOne({
    condition
})

db.collectionName.deleteMany({
    condition
})

db.collectionName.countDocuments()

db.collectionName.find().sort({ field: 1 })

db.collectionName.find().sort({ field: -1 })

db.collectionName.find().limit(2)

db.collectionName.drop()

db.dropDatabase()

exit
```
