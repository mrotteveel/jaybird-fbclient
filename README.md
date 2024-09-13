Firebird Native Client Distribution for Jaybird
===============================================

[![MavenCentral](https://maven-badges.herokuapp.com/maven-central/org.firebirdsql.jdbc/fbclient/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.firebirdsql.jdbc/fbclient/)

Bundle of [Firebird](https://www.firebirdsql.org/) native client libraries for
use with Jaybird 3 and higher.

This bundle packages `fbclient.dll`/`libfbclient.so` for the Windows and Linux
platforms (x86 32- and 64-bit), and can be used with [Jaybird](https://github.com/FirebirdSQL/jaybird)
for the `native` and `local` protocols. It does not support the `embedded`
protocol.

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
        <version>4.0.5.0</version>
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

Download
--------

### Version 4.0.5.0 ###

[fbclient-4.0.5.0.jar](https://repo1.maven.org/maven2/org/firebirdsql/jdbc/fbclient/4.0.5.0/)

### Version 3.0.12.0 ###

[fbclient-3.0.12.0.jar](https://repo1.maven.org/maven2/org/firebirdsql/jdbc/fbclient/3.0.12.0/)

Build information
-----------------

### Version ###

The version has 4 components. The first three are the Firebird version that
sourced the libraries (eg 3.0.4). The last part is a 'build' identifier, which
should usually be 0. The 'build' identifier may be incremented for patches or
new platforms added. 
