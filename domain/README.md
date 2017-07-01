- [Domain Model](/domain/README.md)
  - [Mapping types](/domain/01.md)
  - [Naming strategies](/domain/02.md)
  - [Basic Types](/domain/03/README.md)
    - [Hibernate-provided BasicTypes](/domain/03/01.md)
    - [The @Basic annotation](/domain/03/02.md)
    - [The @Column annotation](/domain/03/03.md)
    - [BasicTypeRegistry](/domain/03/04.md)
    - [Explicit BasicTypes](/domain/03/05.md)
    - [Custom BasicTypes](/domain/03/06.md)
    - [Mapping enums](/domain/03/07.md)
    - [Mapping LOBs](/domain/03/08.md)
    - [Mapping Nationalized Character Data](/domain/03/09.md)
    - [Mapping UUID Values](/domain/03/10.md)
    - [UUID as binary](/domain/03/11.md)
    - [UUID as (var)char](/domain/03/12.md)
    - [PostgeSQL-specific UUID](/domain/03/13.md)
    - [UUID as identifier](/domain/03/14.md)
    - [Mapping Date/Time Values](/domain/03/15.md)
    - [JPA 2.1 AttributeConverters](/domain/03/16.md)
    - [SQL quoted identifiers](/domain/03/17.md)
    - [Generated properties](/domain/03/18.md)
    - [Column transformers: read and write expressions](/domain/03/19.md)
    - [@Formula](/domain/03/20.md)
    - [@Where](/domain/03/21.md)
    - [@Filter](/domain/03/22.md)
    - [@FilterJoinTable](/domain/03/23.md)
    - [@Any mapping](/domain/03/24.md)
    - [@JoinFormula mapping](/domain/03/25.md)
    - [@JoinColumnOrFormula mapping](/domain/03/26.md)
  - [Embeddable types](/domain/04/README.md)
    - [Component / Embedded](/domain/04/01.md)
    - [Multiple embeddable types](/domain/04/02.md)
    - [JPA's AttributeOverride](/domain/04/03.md)
    - [ImplicitNamingStrategy](/domain/04/04.md)
    - [Collections of embeddable types](/domain/04/05.md)
    - [Embeddable types as Map key](/domain/04/06.md)
    - [Embeddable types as identifiers](/domain/04/07.md)
  - [Entity types](/domain/05.md)
  - [Identifiers](/domain/06/README.md)
  - [Associations](/domain/07/README.md)
    - [@ManyToOne](/domain/07/01.md)
    - [@OneToMany](/domain/07/02.md)
    - [@OneToOne](/domain/07/03.md)
    - [@ManyToMany](/domain/07/04.md)
    - [@NotFound association mapping](/domain/07/05.md)


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

