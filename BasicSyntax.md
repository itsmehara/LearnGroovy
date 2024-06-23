### 2. Basic Syntax

#### Variables and Types
Groovy is dynamically typed but also supports static typing.

```groovy
def name = "Groovy"  // Dynamic typing
String language = "Groovy"  // Static typing
int year = 2023
println "Name: $name, Language: $language, Year: $year"
```

#### Basic Operators
Groovy supports all standard arithmetic, relational, and logical operators.

```groovy
def a = 10
def b = 5
println "Addition: ${a + b}"
println "Subtraction: ${a - b}"
println "Multiplication: ${a * b}"
println "Division: ${a / b}"
println "Modulus: ${a % b}"
```

#### Control Structures
Groovy uses control structures similar to those in Java, with some enhancements.

- **If-Else**:
  ```groovy
  def num = 10
  if (num > 0) {
      println "$num is positive"
  } else if (num < 0) {
      println "$num is negative"
  } else {
      println "$num is zero"
  }
  ```

- **Switch**:
  ```groovy
  def x = 2
  switch (x) {
      case 1:
          println "x is one"
          break
      case 2:
          println "x is two"
          break
      default:
          println "x is unknown"
  }
  ```

- **For Loop**:
  ```groovy
  for (i in 1..5) {
      println "Iteration $i"
  }
  ```

- **While Loop**:
  ```groovy
  def count = 1
  while (count <= 5) {
      println "Count is $count"
      count++
  }
  ```
