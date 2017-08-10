# 术语
- object model - application domain model, 也可以粗略称作 persistent classes, 可以有 POJO, Map, xml 等多种表示方式
- relational data model - database model
- hibernate type - org.hibernate.type.Type 的实现类，在 Java type 和 JDBC type 之间做 marshalling
- value type - a piece of data that does not define its own lifecycle. It is, in effect, owned by an entity, which defines its lifecycle.
- persistent attributes - 有状态的 fields/properties(state fields or JavaBean properties)
- instance variables - persistent state of an entity, 即 persistent attributes
- access strategy - 有两种: entity attributes (instance fields)(field-based) / accessors (instance properties)(property-based) 。由 @Id 注解的位置决定使用哪种 access strategy
- components/embeddables - a composition of values


Hibernate 将 type 分两类：
- Value types
- Entity types


value type 又分三类：
- Basic types
- Embeddable types
- Collection types


[状态](/persistence-contexts/README.md), 参见 org.hibernate.event.internal.AbstractSaveEventListener.EntityState
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


bytecode enhancement 参见 [Bytecode Enhancement](/persistence-contexts/02.md)
- run-time enhancement
- build-time enhancement


操作，参见 [Working with detached data](/persistence-contexts/10.md)
- detachment is the process of working with data outside the scope of any persistence context
- reattachment is the process of taking an incoming entity instance that is in detached state and re-associating it with the current persistence context.
- merging is the process of taking an incoming entity instance that is in detached state and copying its data over onto a new managed instance.


relationship ends 参见 [Associations](/domain-model/07/README.md)
- owning side - 在 OneToMany/OneToOne 中也叫 child side/client-side
- inverse/mappedBy side - 在 OneToMany/OneToOne 中也叫 parent side
注意是 client side owns/controls the relationship


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
logMessageFormat=org.example.demo.SimpleMessageFormat
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
package org.example.demo;

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
- https://github.com/hibernate/hibernate-orm/tree/master/documentation/src/main/asciidoc/userguide - 文档源码
- https://github.com/hibernate/hibernate-orm/tree/master/documentation/src/test/java/org/hibernate/userguide - 文档中示例源码
