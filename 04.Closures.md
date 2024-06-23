
### 4. Closures

Closures are anonymous code blocks that can be assigned to variables, passed as arguments, or returned from methods.

#### Defining Closures
```groovy
def greet = { println "Hello, Groovy!" }
greet()
```

#### Passing Parameters to Closures
```groovy
def greet = { name -> println "Hello, $name!" }
greet("Alice")
```

#### Returning Values from Closures
```groovy
def square = { it * it }
println square(4)
```

#### Closure Delegation Strategies
Closures in Groovy have a delegate object that can be used to change the scope of the closure.

```groovy
class Person {
    String name
    void greet() {
        println "Hello, my name is $name"
    }
}

def closure = {
    greet()
}

Person p = new Person(name: 'John')
closure.delegate = p
closure()
```

#### Closures with Collections
Closures are heavily used in Groovy collections for operations like `each`, `find`, `collect`, etc.

```groovy
def numbers = [1, 2, 3, 4, 5]
numbers.each { println it }
def evenNumbers = numbers.findAll { it % 2 == 0 }
println "Even Numbers: $evenNumbers"
def squares = numbers.collect { it * it }
println "Squares: $squares"
```

#### Closure Currying
Currying allows you to fix a number of arguments in a closure.

```groovy
def multiply = { a, b -> a * b }
def multiplyBy2 = multiply.curry(2)
println multiplyBy2(5)  // Output: 10
```
