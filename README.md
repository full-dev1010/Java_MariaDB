# MariaDB Java My Project

<dependency>
    <groupId>wine1993228@gmail.com</groupId>
    <artifactId>my-mariadb-connector-java</artifactId>
    <version>2.7.0</version>
</dependency>
```

### Source code version
* master: based on MariaDB/mariadb-connector-j branch master with redirection support.
* 2.7.0-with-redirection: based on MariaDB/mariadb-connector-j tag 2.7.0 with redirection support.
* 2.6.0-with-redirection: based on MariaDB/mariadb-connector-j tag 2.6.0 with redirection support.
* 2.5.1-with-redirection: based on MariaDB/mariadb-connector-j tag 2.5.1 with redirection support.

**Notice** There is an issue traced for MariaDB/mariadb-connector-j 2.5.2+.
The problem has been fixed on 2.7.0. The recommended branch is 2.7.0-with-redirection or 2.5.1-with-redirection.


```java
    // Load the JDBC driver
    Class.forName("org.mariadb.jdbc.Driver");
    System.out.println("Driver loaded");

    int count = 10;
    String query = "SELECT 1";
    int i=0;
    // Try to connect
    String url = "jdbc:mysql://xxx.mysql.database.azure.com"+
            "?verifyServerCertificate=false"+
            "&useSSL=true"+
            "&requireSSL=true" +
			"&enableRedirect=on";

    Connection connection = DriverManager.getConnection (url, "username", "password");
    double t1 = System.nanoTime();
    Statement s1 = connection.createStatement();
    for(i=0;i<count;i++)
    {
        s1.executeQuery(query);
    }
    double t2 = System.nanoTime();
    System.out.println (" time = " + (t2 - t1)/count/1000000);
    connection.close();
```
