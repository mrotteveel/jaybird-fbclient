Firebird Native Client Distribution for Jaybird
===============================================

[![MavenCentral](https://maven-badges.herokuapp.com/maven-central/org.firebirdsql.jdbc/fbclient/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.firebirdsql.jdbc/fbclient/)

Bundle of [Firebird](https://www.firebirdsql.org/) native client libraries for
use with Jaybird 3 and higher.

This bundle packages `fbclient.dll`/`libfbclient.so` for the following 
platforms:

* Windows (x86, and x86-64)
* Linux (x86, x86-64, and, since 5.0.1.0, aarch64, and arm)
* macOS (since 5.0.1.0: x86-64, and aarch64)

It can be used with [Jaybird](https://github.com/FirebirdSQL/jaybird) for 
the `native` and `local` protocols. It does not support the `embedded` protocol.

Usage
-----

To use this bundle, you need to depend on this library, your preferred 
Jaybird 3 (or higher) version, and the JNA version required by that version of 
Jaybird:

```xml
<dependencies>
    <dependency>
        <groupId>org.firebirdsql.jdbc</groupId>
        <artifactId>fbclient</artifactId>
        <version>5.0.1.1</version>
    </dependency>
    <dependency>
        <groupId>org.firebirdsql.jdbc</groupId>
        <artifactId>jaybird</artifactId>
        <version>5.0.5.java11</version>
    </dependency>
    <dependency>
        <groupId>net.java.dev.jna</groupId>
        <artifactId>jna</artifactId>
        <version>5.14.0</version>
    </dependency>
</dependencies>
```

You can now use the native protocol without having fbclient on the library path:

```java
public class Example {
    public static void main(String[] args) {
        try (Connection connection = DriverManager.getConnection(
                "jdbc:firebird:native:localhost:employee", "user", "password")) {
            // use connection
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

### OS-specific packages

Since version 5.0.1.1, it is possible to only download libraries for a specific
OS and, optionally, architecture. If you add a `classifier` to the Maven
`dependency`, it will only download the JAR with libraries for that specific OS,
or only the library for the specified OS and architecture.

The available classifiers are:

* darwin (macOS)
  * darwin-aarch64
  * darwin-x86
* linux (Linux)
  * linux-aarch64
  * linux-arm
  * linux-x86
  * linux-x86-64
* win32 (Windows)
  * win32-x86
  * win32-x86-64

The names of the classifiers are the technical names used by JNA (Java Native 
Access) for identifying libraries for a specific platform.
    
For example, to only get the Windows 64-bit (x86-64/AMD64) library:

```xml
<dependency>
    <groupId>org.firebirdsql.jdbc</groupId>
    <artifactId>fbclient</artifactId>
    <version>5.0.1.1</version>
    <classifier>win32-x86-64</classifier>
</dependency>
```

Download
--------

### Version 5.0.1.1 ###

[fbclient-5.0.1.1.jar](https://repo1.maven.org/maven2/org/firebirdsql/jdbc/fbclient/5.0.1.1/)

### Version 4.0.5.0 ###

[fbclient-4.0.5.0.jar](https://repo1.maven.org/maven2/org/firebirdsql/jdbc/fbclient/4.0.5.0/)

### Version 3.0.12.0 ###

[fbclient-3.0.12.0.jar](https://repo1.maven.org/maven2/org/firebirdsql/jdbc/fbclient/3.0.12.0/)

Build information
-----------------

### Version ###

The version has 4 components. The first three are the Firebird version that
sourced the libraries (e.g. 3.0.4). The last part is a 'build' identifier, which
should usually be 0. The 'build' identifier may be incremented for patches or
new platforms added. 
