- [Domain Model](/orm/domain/README.md)
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


Identifiers 对应的 database column
- UNIQUE
- NOT NULL - The values cannot be null. For composite ids, no part can be null.
- IMMUTABLE - The values, once inserted, can never be changed


In cases where the values for the PK you have chosen will be updated, Hibernate recommends mapping the mutable value as a natural id, and use a surrogate id for the PK

