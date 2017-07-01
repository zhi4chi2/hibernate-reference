- [Domain Model](/domain-model/README.md)
  - [Mapping types](/domain-model/01.md)
  - [Naming strategies](/domain-model/02.md)
  - [Basic Types](/domain-model/03/README.md)
    - [Hibernate-provided BasicTypes](/domain-model/03/01.md)
    - [The @Basic annotation](/domain-model/03/02.md)
    - [The @Column annotation](/domain-model/03/03.md)
    - [BasicTypeRegistry](/domain-model/03/04.md)
    - [Explicit BasicTypes](/domain-model/03/05.md)
    - [Custom BasicTypes](/domain-model/03/06.md)
    - [Mapping enums](/domain-model/03/07.md)
    - [Mapping LOBs](/domain-model/03/08.md)
    - [Mapping Nationalized Character Data](/domain-model/03/09.md)
    - [Mapping UUID Values](/domain-model/03/10.md)
    - [UUID as binary](/domain-model/03/11.md)
    - [UUID as (var)char](/domain-model/03/12.md)
    - [PostgeSQL-specific UUID](/domain-model/03/13.md)
    - [UUID as identifier](/domain-model/03/14.md)
    - [Mapping Date/Time Values](/domain-model/03/15.md)
    - [JPA 2.1 AttributeConverters](/domain-model/03/16.md)
    - [SQL quoted identifiers](/domain-model/03/17.md)
    - [Generated properties](/domain-model/03/18.md)
    - [Column transformers: read and write expressions](/domain-model/03/19.md)
    - [@Formula](/domain-model/03/20.md)
    - [@Where](/domain-model/03/21.md)
    - [@Filter](/domain-model/03/22.md)
    - [@FilterJoinTable](/domain-model/03/23.md)
    - [@Any mapping](/domain-model/03/24.md)
    - [@JoinFormula mapping](/domain-model/03/25.md)
    - [@JoinColumnOrFormula mapping](/domain-model/03/26.md)
  - [Embeddable types](/domain-model/04/README.md)
  - [Entity types](/domain-model/05.md)
  - [Identifiers](/domain-model/06/README.md)
  - [Associations](/domain-model/07/README.md)


# 测试
src/main/resources/META-INF/persistence.xml
```xml
<persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence
             http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd"
  version="2.1">
  <persistence-unit name="test">
    <properties>
      <property name="javax.persistence.jdbc.url" value="jdbc:p6spy:postgresql://localhost:5432/test" />
      <property name="javax.persistence.jdbc.user" value="postgres" />
      <property name="javax.persistence.jdbc.password" value="postgres" />

      <property name="javax.persistence.schema-generation.database.action" value="drop-and-create" />
    </properties>
  </persistence-unit>
</persistence>
```

