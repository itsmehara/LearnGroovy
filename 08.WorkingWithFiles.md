
### 8. Working with Files and I/O

#### Reading and Writing Files
Groovy makes it easy to read from and write to files.

```groovy
// Writing to a file
new File('example.txt').withWriter('UTF-8') { writer ->
    writer.writeLine 'Hello, Groovy!'
}

// Reading from a file
new File('example.txt').eachLine { line ->
    println line
}
```

#### Working with Directories
Groovy provides utilities for working with directories.

```groovy
def dir = new File('testDir')
dir.mkdir()

new File(dir, 'file1.txt').text = 'Content of file1'
new File(dir, 'file2.txt').text = 'Content of file2'

dir.eachFile { file ->
    println file.name
}
```

#### File System Operations
Perform various file system operations like copying and deleting files.

```groovy
def source = new File('example.txt')
def destination = new File('copy_example.txt')

destination.text = source.text  // Copy file

source.delete()  // Delete file
```

#### Using Streams
Groovy simplifies working with streams for I/O operations.

```groovy
def sourceFile = new File('largefile.txt')
def destFile = new File('largefile_copy.txt')

sourceFile.withInputStream { input ->
    destFile.withOutputStream { output ->
        output << input
    }
}
```

#### Serialization and Deserialization
Serialize and deserialize objects to and from files.

```groovy
import groovy.json.JsonOutput
import groovy.json.JsonSlurper

def data = [name: 'John', age: 30]

// Serialize to JSON
def json = JsonOutput.toJson(data)
new File('data.json').text = json

// Deserialize from JSON
def jsonData = new File('data.json').text
def parsedData = new JsonSlurper().parseText(jsonData)
println parsedData
```

#### Handling File Metadata
Access file metadata like size, modification date, and permissions.

```groovy
def file = new File('example.txt')
println "Size: ${file.size()} bytes"
println "Last modified: ${new Date(file.lastModified())}"
println "Readable: ${file.canRead()}"
println "Writable: ${file.canWrite()}"
```


By covering these sections in detail, you should have a comprehensive understanding of 

object-oriented programming, 
advanced Groovy features, 
scripting with Groovy, 
and working with files and I/O in Groovy. 

Practice each example and experiment with variations to deepen your expertise.
