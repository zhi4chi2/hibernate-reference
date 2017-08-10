- [Domain Model](/orm/domain/README.md)
  - [Mapping types](/orm/domain/01.md)
  - [Naming strategies](/orm/domain/02.md)
  - [Basic Types](/orm/domain/03/README.md)
    - [Hibernate-provided BasicTypes](/orm/domain/03/01.md)
    - [The @Basic annotation](/orm/domain/03/02.md)
    - [The @Column annotation](/orm/domain/03/03.md)
    - [BasicTypeRegistry](/orm/domain/03/04.md)
    - [Explicit BasicTypes](/orm/domain/03/05.md)
    - [Custom BasicTypes](/orm/domain/03/06.md)
    - [Mapping enums](/orm/domain/03/07.md)
    - [Mapping LOBs](/orm/domain/03/08.md)
    - [Mapping Nationalized Character Data](/orm/domain/03/09.md)
    - [Mapping UUID Values](/orm/domain/03/10.md)
    - [UUID as binary](/orm/domain/03/11.md)
    - [UUID as (var)char](/orm/domain/03/12.md)
    - [PostgeSQL-specific UUID](/orm/domain/03/13.md)
    - [UUID as identifier](/orm/domain/03/14.md)
    - [Mapping Date/Time Values](/orm/domain/03/15.md)
    - [JPA 2.1 AttributeConverters](/orm/domain/03/16.md)
    - [SQL quoted identifiers](/orm/domain/03/17.md)
    - [Generated properties](/orm/domain/03/18.md)
    - [Column transformers: read and write expressions](/orm/domain/03/19.md)
    - [@Formula](/orm/domain/03/20.md)
    - [@Where](/orm/domain/03/21.md)
    - [@Filter](/orm/domain/03/22.md)
    - [@FilterJoinTable](/orm/domain/03/23.md)
    - [@Any mapping](/orm/domain/03/24.md)
    - [@JoinFormula mapping](/orm/domain/03/25.md)
    - [@JoinColumnOrFormula mapping](/orm/domain/03/26.md)
  - [Embeddable types](/orm/domain/04/README.md)
    - [Component / Embedded](/orm/domain/04/01.md)
    - [Multiple embeddable types](/orm/domain/04/02.md)
    - [JPA's AttributeOverride](/orm/domain/04/03.md)
    - [ImplicitNamingStrategy](/orm/domain/04/04.md)
    - [Collections of embeddable types](/orm/domain/04/05.md)
    - [Embeddable types as Map key](/orm/domain/04/06.md)
    - [Embeddable types as identifiers](/orm/domain/04/07.md)
  - [Entity types](/orm/domain/05.md)
  - [Identifiers](/orm/domain/06/README.md)
    - [Simple identifiers](/orm/domain/06/01.md)
    - [Composite identifiers](/orm/domain/06/02.md)
    - [Composite identifiers with @EmbeddedId](/orm/domain/06/03.md)
    - [Composite identifiers with @IdClass](/orm/domain/06/04.md)
    - [Composite identifiers with associations](/orm/domain/06/05.md)
    - [Generated identifier values](/orm/domain/06/06.md)
    - [Interpreting AUTO](/orm/domain/06/07.md)
    - [Using sequences](/orm/domain/06/08.md)
    - [Using IDENTITY columns](/orm/domain/06/09.md)
    - [Using identifier table](/orm/domain/06/10.md)
    - [Using UUID generation](/orm/domain/06/11.md)
    - [Optimizers](/orm/domain/06/12.md)
    - [Using @GenericGenerator](/orm/domain/06/13.md)
    - [Derived Identifiers](/orm/domain/06/14.md)
  - [Associations](/orm/domain/07/README.md)
    - [@ManyToOne](/orm/domain/07/01.md)
    - [@OneToMany](/orm/domain/07/02.md)
    - [@OneToOne](/orm/domain/07/03.md)
    - [@ManyToMany](/orm/domain/07/04.md)
    - [@NotFound association mapping](/orm/domain/07/05.md)
  - [Collections](/orm/domain/08/README.md)
    - [Collections as a value type](/orm/domain/08/01.md)
    - [Collections of value types](/orm/domain/08/02.md)
    - [Collections of entities](/orm/domain/08/03.md)
    - [Bags](/orm/domain/08/04.md)
    - [Ordered Lists](/orm/domain/08/05.md)
    - [Sets](/orm/domain/08/06.md)


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

