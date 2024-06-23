### 9. Exception Handling

#### Basic Exception Handling

Groovy's exception handling is similar to Java, using `try`, `catch`, and `finally` blocks.

```groovy
try {
    int result = 10 / 0
    println "Result: $result"
} catch (ArithmeticException e) {
    println "Caught an ArithmeticException: ${e.message}"
} finally {
    println "This will always execute"
}
```

#### Multiple Catch Blocks

You can catch multiple exceptions in a single `try` block.

```groovy
try {
    int[] arr = [1, 2, 3]
    println arr[5]
} catch (ArrayIndexOutOfBoundsException e) {
    println "Caught an ArrayIndexOutOfBoundsException: ${e.message}"
} catch (Exception e) {
    println "Caught a generic exception: ${e.message}"
}
```

#### Nested Exception Handling

Exception handling can be nested within other `try` blocks.

```groovy
try {
    try {
        int result = 10 / 0
    } catch (ArithmeticException e) {
        println "Inner catch: ArithmeticException: ${e.message}"
        throw new RuntimeException("Wrapped Exception", e)
    }
} catch (RuntimeException e) {
    println "Outer catch: RuntimeException: ${e.message}"
    e.printStackTrace()
}
```

#### Custom Exceptions

You can define your own custom exception classes.

```groovy
class CustomException extends Exception {
    CustomException(String message) {
        super(message)
    }
}

try {
    throw new CustomException("This is a custom exception")
} catch (CustomException e) {
    println "Caught a CustomException: ${e.message}"
}
```

#### Exception Propagation

Exceptions can be propagated up the call stack.

```groovy
def divide(int a, int b) {
    if (b == 0) {
        throw new ArithmeticException("Division by zero")
    }
    return a / b
}

try {
    println divide(10, 0)
} catch (ArithmeticException e) {
    println "Caught an ArithmeticException: ${e.message}"
}
```

#### Using `throw` Keyword

The `throw` keyword is used to explicitly throw an exception.

```groovy
def checkAge(int age) {
    if (age < 18) {
        throw new IllegalArgumentException("Age must be 18 or older")
    }
    println "Age is valid"
}

try {
    checkAge(16)
} catch (IllegalArgumentException e) {
    println "Caught an IllegalArgumentException: ${e.message}"
}
```

#### Rethrowing Exceptions

You can catch and then rethrow exceptions.

```groovy
try {
    try {
        throw new IOException("IO error")
    } catch (IOException e) {
        println "Caught IOException: ${e.message}"
        throw e  // Rethrow the exception
    }
} catch (IOException e) {
    println "Caught rethrown IOException: ${e.message}"
}
```

#### Using `assert` for Simple Exception Handling

Groovy's `assert` can be used for simple checks.

```groovy
def divide(int a, int b) {
    assert b != 0 : "Divider cannot be zero"
    a / b
}

try {
    println divide(10, 0)
} catch (AssertionError e) {
    println "Caught AssertionError: ${e.message}"
}
```

### 10. Functional Programming with Groovy

#### Closures

Closures are the foundation of functional programming in Groovy.

```groovy
def greet = { name -> "Hello, $name!" }
println greet("Groovy")
```

#### Higher-Order Functions

Functions that take other functions as arguments or return functions.

```groovy
def applyTwice(Closure closure, def value) {
    closure(closure(value))
}

def doubleIt = { it * 2 }
println applyTwice(doubleIt, 5)  // Output: 20
```

#### Currying

Currying allows you to create new functions by fixing some arguments of the original function.

```groovy
def multiply = { a, b -> a * b }
def multiplyBy2 = multiply.curry(2)
println multiplyBy2(5)  // Output: 10
```

#### Using Collections with Closures

Closures can be used with collections for various operations like `each`, `collect`, `find`, `findAll`, etc.

```groovy
def numbers = [1, 2, 3, 4, 5]
numbers.each { println it }

def squares = numbers.collect { it * it }
println squares

def evenNumbers = numbers.findAll { it % 2 == 0 }
println evenNumbers
```

#### Memoization

Memoization is a technique to cache results of expensive function calls.

```groovy
def factorial
factorial = { int n ->
    if (n <= 1) return 1
    return n * factorial(n - 1)
}.memoize()

println factorial(5)  // Output: 120
println factorial(6)  // Output: 720, but faster due to memoization
```

#### Groovy Built-in Methods

Groovy provides many built-in methods for functional programming, such as `collect`, `find`, `findAll`, `inject`, etc.

```groovy
def words = ['Groovy', 'is', 'great']
println words.find { it.startsWith('g') }  // Output: great

def lengths = words.collect { it.length() }
println lengths  // Output: [6, 2, 5]

def totalLength = words.inject(0) { acc, word -> acc + word.length() }
println totalLength  // Output: 13
```

#### Recursive Closures

Closures can be recursive in Groovy.

```groovy
def factorial
factorial = { int n -> n <= 1 ? 1 : n * factorial(n - 1) }

println factorial(5)  // Output: 120
```

#### Using `spread` and `*.` operator

The `*.` operator (spread operator) is used to apply a method to all elements of a collection.

```groovy
def list = [[1, 2], [3, 4], [5, 6]]
println list*.size()  // Output: [2, 2, 2]

def people = [['name': 'Alice'], ['name': 'Bob']]
println people*.name  // Output: [Alice, Bob]
```

### 11. Groovy and XML/JSON Processing

#### Parsing XML with `XmlSlurper`

Groovy's `XmlSlurper` provides a simple way to parse XML.

```groovy
def xml = '''
<books>
    <book>
        <title>Groovy in Action</title>
        <author>Dierk König</author>
    </book>
    <book>
        <title>Making Java Groovy</title>
        <author>Ken Kousen</author>
    </book>
</books>
'''

def books = new XmlSlurper().parseText(xml)
books.book.each {
    println "Title: ${it.title}, Author: ${it.author}"
}
```

#### Creating XML with `MarkupBuilder`

`MarkupBuilder` is used to create XML.

```groovy
import groovy.xml.MarkupBuilder

def writer = new StringWriter()
def xml = new MarkupBuilder(writer)

xml.books {
    book {
        title 'Groovy in Action'
        author 'Dierk König'
    }
    book {
        title 'Making Java Groovy'
        author 'Ken Kousen'
    }
}

println writer.toString()
```

#### Parsing JSON with `JsonSlurper`

Groovy's `JsonSlurper` provides a simple way to parse JSON.

```groovy
import groovy.json.JsonSlurper

def json = '''
{
    "books": [
        {"title": "Groovy in Action", "author": "Dierk König"},
        {"title": "Making Java Groovy", "author": "Ken Kousen"}
    ]
}
'''

def books = new JsonSlurper().parseText(json)
books.books.each {
    println "Title: ${it.title}, Author: ${it.author}"
}
```

#### Creating JSON with `JsonBuilder`

`JsonBuilder` is used to create JSON.

```groovy
import groovy.json.JsonBuilder

def builder = new JsonBuilder()
builder.books {
    book {
        title 'Groovy in Action'
        author 'Dierk König'
    }
    book {
        title 'Making Java Groovy'
        author 'Ken Kousen'
    }
}

println builder.toPrettyString()
```

#### Reading JSON from a File

Reading JSON content from a file.

```groovy
def jsonFile = new File('books.json')
def jsonContent = new JsonSlurper().parse(jsonFile)

jsonContent.books.each {
    println "Title: ${it.title}, Author: ${it.author}"
}
```

#### Writing JSON to a File

Writing JSON content to a file.

```groovy
import groovy.json.JsonBuilder

def builder = new JsonBuilder()
builder.books {
    book {
        title 'Groovy in Action'
        author 'Dierk König'
    }
    book {
        title 'Making Java Groovy'
        author 'Ken Kousen'
    }
}

new File('books.json').write(builder.toPrettyString())
```

#### Using `@Canonical` for Simple JSON Conversion

The `@Canonical` annotation simplifies conversion between JSON and Groovy objects.

```groovy
import groovy.transform.Canonical
import groovy.json.Json

Output

@Canonical
class Book {
    String title
    String author
}

def book = new Book('Groovy in Action', 'Dierk König')
println JsonOutput.toJson(book)
```

#### Using Streaming JSON

For large JSON documents, Groovy provides streaming capabilities.

```groovy
import groovy.json.JsonSlurper
import groovy.json.JsonOutput

def jsonContent = new File('large.json').text
def parser = new JsonSlurper().setParseOptions(JsonSlurper.LazyMap.NO_LAZY_MAP)
def parsedJson = parser.parseText(jsonContent)

parsedJson.each { item ->
    println JsonOutput.prettyPrint(JsonOutput.toJson(item))
}
```

### 12. Groovy and Databases

#### Connecting to a Database

Using Groovy's `Sql` class to connect to a database.

```groovy
@GrabConfig(systemClassLoader=true)
@Grab('org.hsqldb:hsqldb:2.5.1')

import groovy.sql.Sql

def db = Sql.newInstance('jdbc:hsqldb:mem:sampleDB', 'sa', '', 'org.hsqldb.jdbcDriver')
db.execute('CREATE TABLE books (id INT, title VARCHAR(100), author VARCHAR(100))')
println "Database connected"
```

#### Executing Queries

Executing SQL queries to interact with the database.

```groovy
db.execute("INSERT INTO books VALUES (1, 'Groovy in Action', 'Dierk König')")
db.execute("INSERT INTO books VALUES (2, 'Making Java Groovy', 'Ken Kousen')")

db.eachRow('SELECT * FROM books') { row ->
    println "ID: ${row.id}, Title: ${row.title}, Author: ${row.author}"
}
```

#### Using Parameters in Queries

Using parameters to prevent SQL injection.

```groovy
def title = 'Groovy in Action'
def author = 'Dierk König'

db.execute("INSERT INTO books (id, title, author) VALUES (?, ?, ?)", [3, title, author])

db.eachRow('SELECT * FROM books WHERE author = ?', [author]) { row ->
    println "ID: ${row.id}, Title: ${row.title}, Author: ${row.author}"
}
```

#### Transactions

Using transactions to ensure data integrity.

```groovy
db.withTransaction {
    db.execute("INSERT INTO books VALUES (4, 'Groovy for Java Developers', 'Unknown')")
    db.execute("INSERT INTO books VALUES (5, 'Beginning Groovy and Grails', 'Christopher Judd')")
}

db.eachRow('SELECT * FROM books') { row ->
    println "ID: ${row.id}, Title: ${row.title}, Author: ${row.author}"
}
```

#### Handling Result Sets

Handling result sets from database queries.

```groovy
def books = db.rows('SELECT * FROM books')
books.each {
    println "ID: ${it.id}, Title: ${it.title}, Author: ${it.author}"
}
```

#### Using Groovy's GORM

GORM (Groovy Object-Relational Mapping) is a powerful tool for database operations in Groovy.

```groovy
@Grab('org.grails:grails-datastore-gorm-hibernate5:7.0.4')
@Grab('org.grails:grails-datastore-core:7.0.4')

import grails.gorm.*

@Entity
class Book {
    String title
    String author
}

def datastore = new DatastoreBuilder().build()
datastore.connect()

def book = new Book(title: 'Groovy in Action', author: 'Dierk König')
book.save()

Book.list().each {
    println "Title: ${it.title}, Author: ${it.author}"
}
```

#### Performing CRUD Operations

CRUD (Create, Read, Update, Delete) operations using Groovy's `Sql` class.

```groovy
// Create
db.execute("INSERT INTO books VALUES (6, 'Practical Grails 3', 'Eric Helgeson')")

// Read
db.eachRow('SELECT * FROM books WHERE id = 6') { row ->
    println "ID: ${row.id}, Title: ${row.title}, Author: ${row.author}"
}

// Update
db.execute("UPDATE books SET author = 'Eric Helgeson and Others' WHERE id = 6")

// Delete
db.execute("DELETE FROM books WHERE id = 6")
```

#### Using Groovy with NoSQL Databases

Groovy can also interact with NoSQL databases like MongoDB.

```groovy
@Grab(group='org.mongodb', module='mongodb-driver-sync', version='4.4.1')

import com.mongodb.client.MongoClients

def client = MongoClients.create('mongodb://localhost:27017')
def database = client.getDatabase('testDB')
def collection = database.getCollection('books')

def document = new org.bson.Document('title', 'Groovy in Action').append('author', 'Dierk König')
collection.insertOne(document)

collection.find().each {
    println "Title: ${it.getString('title')}, Author: ${it.getString('author')}"
}
```

By covering these sections in detail, you will gain a comprehensive understanding of 
exception handling, 
functional programming, 
XML/JSON processing, 
and database interactions 
in Groovy. 

Practice each example and experiment with variations to deepen your expertise.
