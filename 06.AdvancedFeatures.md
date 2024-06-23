
### 6. Advanced Groovy Features

#### Meta-programming
Meta-programming allows modifying the behavior of classes at runtime.

```groovy
class Person {
    String name
}

Person.metaClass.greet = { -> "Hello, $name" }

def person = new Person(name: 'John')
println person.greet()
```

#### AST Transformations
AST transformations are compile-time transformations of the Abstract Syntax Tree.

```groovy
import groovy.transform.ToString

@ToString
class Book {
    String title
    String author
}

def book = new Book(title: 'Groovy in Action', author: 'Dierk König')
println book.toString()
```

#### Groovy Categories
Categories provide a way to add methods to existing classes temporarily.

```groovy
class StringUtil {
    static String shout(String self) {
        self.toUpperCase() + "!"
    }
}

use(StringUtil) {
    println "hello".shout()
}
```

#### Traits
Traits are a way to compose behavior in Groovy.

```groovy
trait Flying {
    void fly() {
        println "Flying"
    }
}

class Bird implements Flying {}

def bird = new Bird()
bird.fly()
```
