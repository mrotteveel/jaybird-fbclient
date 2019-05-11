Firebird Native Client Distribution for Jaybird
===============================================

Bundle of Firebird native client libraries for use with Jaybird 3 and higher.

This bundle packages `fbclient.dll`/`libfbclient.so` for the Windows and Linux
platforms (32 and 64 bit), and can be used with [Jaybird](https://github.com/FirebirdSQL/jaybird)
for the `native` and `local` protocols. It does not support `embedded` protocol.

Usage
-----

To use this bundle, you need to depend on this library and your preferred 
Jaybird 3 (or higher) version and the JNA version required by that version of 
Jaybird:

```xml
<dependencies>
    <dependency>
        <groupId>org.firebirdsql.jdbc</groupId>
        <artifactId>fbclient</artifactId>
        <version>3.0.4.0</version>
    </dependency>
    <dependency>
        <groupId>org.firebirdsql.jdbc</groupId>
        <artifactId>jaybird-jdk18</artifactId>
        <version>3.0.5</version>
    </dependency>
    <dependency>
        <groupId>net.java.dev.jna</groupId>
        <artifactId>jna</artifactId>
        <version>4.4.0</version>
    </dependency>
</dependencies>
```

When connecting, you can now use the native protocol without having fbclient on
your classpath:

```java
public class Example {
    public static void main(String[] args) {
        try (Connection connection = DriverManager.getConnection(
                "jdbc:firebirdsql:native:localhost:employee", "user", "password")) {
            // use connection
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

Build information
-----------------

### Version ###

The version has 4 components. The first three are the Firebird version that
sourced the libraries (eg 3.0.4). The last part is a 'build' identifier, which
should usually be 0. The 'build' identifier may be incremented for patches or
new platforms added. 
