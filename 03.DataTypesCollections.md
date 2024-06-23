
### 3. Data Types and Collections

#### Strings and GStrings
Groovy enhances Java's `String` class with additional methods and introduces `GString` for string interpolation.

```groovy
def name = "Groovy"
def message = "Hello, ${name}!"
println message
println name.toUpperCase()
println name.reverse()
```

#### Numbers
Groovy simplifies handling numbers and provides built-in methods for common operations.

```groovy
def num = 10
println "Square root of $num: ${Math.sqrt(num)}"
println "Power of $num^2: ${num**2}"
```

#### Lists
Groovy lists are like Python lists and support various operations.

```groovy
def fruits = ['Apple', 'Banana', 'Cherry']
println fruits
fruits << 'Date'
println fruits[1]
fruits.each { println it }
```

#### Maps
Maps in Groovy are similar to Python dictionaries.

```groovy
def person = [name: 'John', age: 30, city: 'New York']
println person
println person['name']
person.each { key, value -> println "$key: $value" }
```

#### Ranges
Ranges represent sequences of values.

```groovy
def range = 1..5
println range
println range.contains(3)
range.each { println it }
```

#### Arrays
Arrays in Groovy can be created like in Java.

```groovy
String[] names = ['Alice', 'Bob', 'Charlie']
println names
println names[0]
```
