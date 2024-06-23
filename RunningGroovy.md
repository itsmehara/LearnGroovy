### Groovy Code File Extension and Running Groovy Code

#### File Extension
Groovy code files typically have the `.groovy` extension. This is similar to how Python files use `.py` and Java files use `.java`.

#### Running Groovy Code

##### 1. Using the Groovy Command Line
Groovy provides a command-line interface to run Groovy scripts directly.

1. **Create a Groovy File**:
   Create a file with the `.groovy` extension, for example, `HelloWorld.groovy`.

   ```groovy
   // HelloWorld.groovy
   println "Hello, Groovy!"
   ```

2. **Run the Groovy Script**:
   Open your terminal or command prompt and navigate to the directory where the `HelloWorld.groovy` file is located. Then run the script using the `groovy` command:

   ```sh
   groovy HelloWorld.groovy
   ```

##### 2. Using the Groovy Console
Groovy provides an interactive console (REPL) for testing and running Groovy code snippets.

1. **Open the Groovy Console**:
   Type `groovyConsole` in your terminal or command prompt.

   ```sh
   groovyConsole
   ```

2. **Write and Execute Code**:
   You can write Groovy code directly in the console and execute it.

##### 3. Using Integrated Development Environments (IDEs)
Several IDEs support Groovy development, providing features like syntax highlighting, code completion, and debugging.

- **IntelliJ IDEA**:
  1. **Download and Install IntelliJ IDEA**:
     You can download IntelliJ IDEA from the [official website](https://www.jetbrains.com/idea/).

  2. **Create a New Groovy Project**:
     - Open IntelliJ IDEA and select "Create New Project".
     - Choose "Groovy" from the list of project templates.
     - Follow the wizard to set up your project.

  3. **Write and Run Groovy Code**:
     - Create a new Groovy script or class file by right-clicking on the project and selecting "New" -> "Groovy Script".
     - Write your Groovy code in the editor.
     - Right-click on the Groovy file and select "Run".

- **Eclipse with Groovy Plugin**:
  1. **Download and Install Eclipse**:
     You can download Eclipse from the [official website](https://www.eclipse.org/downloads/).

  2. **Install the Groovy Plugin**:
     - Open Eclipse and go to "Help" -> "Eclipse Marketplace".
     - Search for "Groovy" and install the Groovy Development Tools (GDT).

  3. **Create a New Groovy Project**:
     - Go to "File" -> "New" -> "Other" -> "Groovy Project".
     - Follow the wizard to set up your project.

  4. **Write and Run Groovy Code**:
     - Create a new Groovy script or class file by right-clicking on the project and selecting "New" -> "Groovy Script".
     - Write your Groovy code in the editor.
     - Right-click on the Groovy file and select "Run As" -> "Groovy Script".

##### 4. Using Gradle
Gradle is a build tool that can be used to run Groovy scripts as part of a build process.

1. **Create a `build.gradle` File**:
   ```groovy
   apply plugin: 'groovy'

   repositories {
       mavenCentral()
   }

   dependencies {
       implementation 'org.codehaus.groovy:groovy-all:3.0.9'
   }

   task runScript(type: JavaExec) {
       main = '-jar'
       args = ["src/main/groovy/HelloWorld.groovy"]
       classpath = sourceSets.main.runtimeClasspath
   }
   ```

2. **Create the Groovy Script**:
   Place your Groovy script in the `src/main/groovy` directory.

   ```groovy
   // src/main/groovy/HelloWorld.groovy
   println "Hello, Groovy with Gradle!"
   ```

3. **Run the Groovy Script Using Gradle**:
   Open your terminal, navigate to the project directory, and run the Gradle task:

   ```sh
   gradle runScript
   ```

### Environment Setup

1. **Install Java Development Kit (JDK)**:
   Groovy runs on the Java Virtual Machine (JVM), so you need to have the JDK installed. You can download it from [Oracle's website](https://www.oracle.com/java/technologies/javase-downloads.html) or use OpenJDK from [AdoptOpenJDK](https://adoptopenjdk.net/).

2. **Install Groovy**:
   Use SDKMAN to install Groovy, which simplifies managing different versions of Groovy and other JVM tools.

   ```sh
   sdk install groovy
   ```

3. **Verify Installation**:
   Check the installation by running:

   ```sh
   groovy -version
   ```

4. **Setting Up an IDE**:
   - **IntelliJ IDEA** and **Eclipse** are popular choices for Groovy development. 
   - Follow the installation and setup steps provided above to configure your preferred IDE.

### Example Workflow

1. **Write Groovy Code**:
   Create a file named `HelloWorld.groovy` and write your Groovy code.

   ```groovy
   // HelloWorld.groovy
   println "Hello, Groovy!"
   ```

2. **Run the Code**:
   Use the Groovy command line, Groovy console, or your IDE to run the script.

   ```sh
   groovy HelloWorld.groovy
   ```

3. **Iterate and Debug**:
   Make changes to your code, run it again, and use the debugging tools provided by your IDE to fix any issues.

By following these steps, 
you can set up your environment, 
write, and run Groovy code efficiently.
