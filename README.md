# Maven Hello World

### Creating Project

Create a maven project using quickstart 1.4 archetype.

```shell
$ mvn archetype:generate -DgroupId=org.rogamba.mavenhello -DartifactId=maven-hello -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 -DinteractiveMode=false
```

Modify /src/main/java/org/rogamba/mavenhello/App.java, add two lines of code to use slf4j logger:

```java
import org.slf4j.*;
Logger logger = LoggerFactory.getLogger(App.class);
logger.info("Hello World!");
```

Add slf4j dependencies to the pom.xml file, remove "test" from the scope tag:

```text
<!-- https://mvnrepository.com/artifact/org.slf4j/slf4j-api -->
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-api</artifactId>
    <version>1.7.28</version>
</dependency>
<!-- https://mvnrepository.com/artifact/org.slf4j/slf4j-simple -->
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>slf4j-simple</artifactId>
    <version>1.7.28</version>
</dependency>
```

Compile and download dependencies with:

```shell
$ mvn compile
```

Package the application to a .jar file

```shell
$ mvn package
```

Execute the application specifying the jar file to include in the classpath:

```shell
$ java -cp target/maven-hello-1.0-SNAPSHOT.jar: org.rogamba.mavenhello.App
```

Output
```text
Hello World!
Exception in thread "main" java.lang.NoClassDefFoundError: org/slf4j/LoggerFactory
	at org.rogamba.mavenhello.App.main(App.java:13)
Caused by: java.lang.ClassNotFoundException: org.slf4j.LoggerFactory
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:583)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:521)
	... 1 more
```

