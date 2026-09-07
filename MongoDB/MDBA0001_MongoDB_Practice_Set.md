# Practice Set with MongoDB

**Aim:** Create a MongoDB database to store and perform different
operations on books available in a college library.

## Database and Collection

| Item | Name |
| --- | --- |
| Database | `libraryDB` |
| Collection | `books` |


------------------------------------------------------------------------

# Data to be Inserted

Each book document should contain the following fields:

| Field | Description | Data Type |
| --- | --- | --- |
| `bookId` | Unique number assigned to the book | Number |
| `title` | Name of the book | String |
| `author` | Name of the author | String |
| `category` | Category of the book | String |
| `price` | Price of the book | Number |

Use the following data:

| `bookId` | `title` | `author` | `category` | `price` |
| ---: | --- | --- | --- | ---: |
| 101 | Database Systems | R. Kumar | Database | 650 |
| 102 | Web Technology | A. Patel | Web Development | 450 |
| 103 | Python Programming | S. Shah | Programming | 550 |
| 104 | JavaScript Basics | K. Mehta | Web Development | 400 |

> **Note:** Do not manually provide the `_id` field. MongoDB will
> automatically generate a unique `_id` for each document.

------------------------------------------------------------------------

# Questions with Answers

## 1. Create/select the `libraryDB` database.

**Answer:**

``` javascript
use libraryDB
```

------------------------------------------------------------------------

## 2. Create the `books` collection.

**Answer:**

``` javascript
db.createCollection("books")
```

------------------------------------------------------------------------

## 3. Insert the book having `bookId` 101 using `insertOne()`.

**Data to insert:**

``` text
bookId   : 101
title    : Database Systems
author   : R. Kumar
category : Database
price    : 650
```

**Answer:**

``` javascript
db.books.insertOne({
    bookId: 101,
    title: "Database Systems",
    author: "R. Kumar",
    category: "Database",
    price: 650
})
```

------------------------------------------------------------------------

## 4. Insert the remaining three books using `insertMany()`.

**Data to insert:**

| `bookId` | `title` | `author` | `category` | `price` |
| ---: | --- | --- | --- | ---: |
| 102 | Web Technology | A. Patel | Web Development | 450 |
| 103 | Python Programming | S. Shah | Programming | 550 |
| 104 | JavaScript Basics | K. Mehta | Web Development | 400 |

**Answer:**

``` javascript
db.books.insertMany([
    {
        bookId: 102,
        title: "Web Technology",
        author: "A. Patel",
        category: "Web Development",
        price: 450
    },
    {
        bookId: 103,
        title: "Python Programming",
        author: "S. Shah",
        category: "Programming",
        price: 550
    },
    {
        bookId: 104,
        title: "JavaScript Basics",
        author: "K. Mehta",
        category: "Web Development",
        price: 400
    }
])
```

------------------------------------------------------------------------

## 5. Display all books.

**Answer:**

``` javascript
db.books.find()
```

------------------------------------------------------------------------

## 6. Find the book having `bookId` 102.

**Answer:**

``` javascript
db.books.findOne({
    bookId: 102
})
```

**Expected book:**

``` javascript
{
    bookId: 102,
    title: "Web Technology",
    author: "A. Patel",
    category: "Web Development",
    price: 450
}
```

The actual document will also contain the `_id` automatically generated
by MongoDB.

------------------------------------------------------------------------

## 7. Find one book using its `_id`.

**Answer:**

First display the documents:

``` javascript
db.books.find()
```

Copy the `_id` of any one document.

For example, if MongoDB displays:

``` javascript
_id: ObjectId("68b4c1a21a23456789abcdef")
```

Find that document using:

``` javascript
db.books.findOne({
    _id: ObjectId("68b4c1a21a23456789abcdef")
})
```

> Replace the example ObjectId with the actual `_id` generated on your
> system.

------------------------------------------------------------------------

## 8. Display books having `price > 500`.

**Answer:**

``` javascript
db.books.find({
    price: { $gt: 500 }
})
```

This condition matches:

-   Database Systems -- ₹650
-   Python Programming -- ₹550

------------------------------------------------------------------------

## 9. Display books having `price >= 500`.

**Answer:**

``` javascript
db.books.find({
    price: { $gte: 500 }
})
```

------------------------------------------------------------------------

## 10. Display books having `price < 500`.

**Answer:**

``` javascript
db.books.find({
    price: { $lt: 500 }
})
```

This condition matches:

-   Web Technology -- ₹450
-   JavaScript Basics -- ₹400

------------------------------------------------------------------------

## 11. Display books having `price <= 500`.

**Answer:**

``` javascript
db.books.find({
    price: { $lte: 500 }
})
```

------------------------------------------------------------------------

## 12. Find books whose category is either `Programming` or `Web Development` using `$in`.

**Answer:**

``` javascript
db.books.find({
    category: {
        $in: ["Programming", "Web Development"]
    }
})
```

------------------------------------------------------------------------

## 13. Change the price of the book having `bookId` 102 from `450` to `500` using `$set`.

**Answer:**

``` javascript
db.books.updateOne(
    { bookId: 102 },
    { $set: { price: 500 } }
)
```

------------------------------------------------------------------------

## 14. Display the book having `bookId` 102 to verify the updated price.

**Answer:**

``` javascript
db.books.findOne({
    bookId: 102
})
```

The updated price should now be:

``` text
price: 500
```

------------------------------------------------------------------------

## 15. Sort all books according to price.

**Answer -- Ascending Order:**

``` javascript
db.books.find().sort({
    price: 1
})
```

**Answer -- Descending Order:**

``` javascript
db.books.find().sort({
    price: -1
})
```

> `1` represents ascending order and `-1` represents descending order.

------------------------------------------------------------------------

## 16. Count the total number of books.

**Answer:**

``` javascript
db.books.countDocuments()
```

**Expected Result:**

``` text
4
```

------------------------------------------------------------------------

## 17. Delete the book having `bookId` 104.

**Answer:**

``` javascript
db.books.deleteOne({
    bookId: 104
})
```

------------------------------------------------------------------------

## 18. Display all remaining books.

**Answer:**

``` javascript
db.books.find()
```

After deleting `bookId` 104, the collection should contain **3 books**.



# Try Yourself

19. Display all books whose price is not equal to `500` using `$ne`.

20. Display books that do not belong to the `Database` and `Programming` categories using `$nin`.

21. Display books having a price less than `450` OR greater than `600` using `$or`.

22. Increase the price of the book having `bookId` 103 by `50` using `$inc`.

23. Display only the first two books using `limit()`.

24. Display only the `title` and `price` of all books and hide the `_id` field using projection.
