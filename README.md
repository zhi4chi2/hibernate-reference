# 术语
- object model - application domain model
- relational data model - database model


[状态](/persistence-contexts/README.md)
- transient
- managed/persistent
- detached
- removed


lazy loading 参见 [Bytecode Enhancement](/persistence-contexts/02.md)
- proxy-based
- lazy attribute loading


dirty calculation 参见 [Bytecode Enhancement](/persistence-contexts/02.md)
- diff-based
- in-line bytecode-enhanced  dirty tracking


# 测试项目
pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <parent>
    <groupId>org.example.demo</groupId>
    <artifactId>demo-parent</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <relativePath>../pom.xml</relativePath>
  </parent>

  <artifactId>demo-hibernate</artifactId>
  <packaging>jar</packaging>

  <name>demo-hibernate</name>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <hibernate.version>5.2.10.Final</hibernate.version>
  </properties>

  <dependencies>
    <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-core</artifactId>
      <version>${hibernate.version}</version>
    </dependency>
    <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-entitymanager</artifactId>
      <version>${hibernate.version}</version>
    </dependency>
    <dependency>
      <groupId>org.postgresql</groupId>
      <artifactId>postgresql</artifactId>
      <version>9.4.1212</version>
    </dependency>

    <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
    </dependency>
    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
    </dependency>
    <dependency>
      <groupId>p6spy</groupId>
      <artifactId>p6spy</artifactId>
      <version>2.1.4</version>
    </dependency>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```


src/main/resources/spy.properties
```
databaseDialectDateFormat=yyyy-MM-dd HH:mm:ss
dateformat=yyyy-MM-dd HH:mm:ss
append=false
logMessageFormat=org.example.SimpleMessageFormat
```


src/main/resources/logback.xml
```xml
<configuration>
  <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
    <encoder>
      <pattern>[%thread] %-5level %logger- %msg%n</pattern>
    </encoder>
  </appender>

  <logger name="org.hibernate.SQL" level="debug" />
  <logger name="org.hibernate.type" level="trace" />

  <root level="info">
    <appender-ref ref="STDOUT" />
  </root>
</configuration>
```


```java
package org.example;

import com.p6spy.engine.common.P6Util;
import com.p6spy.engine.spy.appender.MessageFormattingStrategy;

public class SimpleMessageFormat implements MessageFormattingStrategy {
    @Override
    public String formatMessage(int connectionId, String now, long elapsed, String category, String prepared, String sql) {
        if (sql == null || sql.trim().isEmpty()) {
            return P6Util.singleLine(prepared);
        } else {
            return P6Util.singleLine(sql);
        }
    }
}
```


# Reference
- hibernate-release-5.2.10.Final/documentation/userguide/html_single/Hibernate_User_Guide.html
