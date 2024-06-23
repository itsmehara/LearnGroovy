
### 7. Groovy Scripting

#### Using Groovy as a Scripting Language
Groovy scripts can be written to automate tasks and run in various environments.

```groovy
// Hello.groovy
println "Hello, Groovy Script!"
```

Run this script using the Groovy command:
```sh
groovy Hello.groovy
```

#### Running Groovy Scripts
Groovy scripts can be executed directly from the command line or from within applications.

```groovy
// ScriptExample.groovy
def greet(name) {
    println "Hello, $name!"
}

greet('Alice')
```

```sh
groovy ScriptExample.groovy
```

#### Integrating Groovy with Other Scripting Languages
Groovy can interact with other scripting languages, such as JavaScript or Python, using JSR-223 (Java Scripting API).

```groovy
import javax.script.ScriptEngineManager

def engine = new ScriptEngineManager().getEngineByName("nashorn")
engine.eval('print("Hello from JavaScript")')
```

#### Using Groovy Scripts in Build Tools
Groovy scripts can be used in build tools like Gradle for custom tasks.

```groovy
// build.gradle
task hello {
    doLast {
        println 'Hello from Gradle'
    }
}
```

Run the task using:
```sh
gradle hello
```
