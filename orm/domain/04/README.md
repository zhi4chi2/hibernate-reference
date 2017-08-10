- [Domain Model](/orm/domain/README.md)
  - [Embeddable types](/orm/domain/04/README.md)
    - [Component / Embedded](/orm/domain/04/01.md)
    - [Multiple embeddable types](/orm/domain/04/02.md)
    - [JPA's AttributeOverride](/orm/domain/04/03.md)
    - [ImplicitNamingStrategy](/orm/domain/04/04.md)
    - [Collections of embeddable types](/orm/domain/04/05.md)
    - [Embeddable types as Map key](/orm/domain/04/06.md)
    - [Embeddable types as identifiers](/orm/domain/04/07.md)


An embeddable type is another form of value type, and its lifecycle is bound to a parent entity type, therefore inheriting the attribute access(see Access strategies) from its parent


旧版 Hibernate 将 embeddable types 称为 components, JPA 称为 embeddables


Embeddable types can be made up of basic values as well as associations, with the caveat that, when used as collection elements, they cannot define collections themselves.


embeddable types 可以由 basic value 以及 associations 组成。如果用作 collection elements 则不能定义 collections (Embeddable types can be made up of basic values as well as associations, with the caveat that, when used as collection elements, they cannot define collections themselves.)



