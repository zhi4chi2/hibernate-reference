Identifiers 对应的 database column
- UNIQUE
- NOT NULL - The values cannot be null. For composite ids, no part can be null.
- IMMUTABLE - The values, once inserted, can never be changed


In cases where the values for the PK you have chosen will be updated, Hibernate recommends mapping the mutable value as a natural id, and use a surrogate id for the PK


- [Domain Model](/domain/README.md)
  - [Identifiers](/domain/06/README.md)
    - [Simple identifiers](/domain/06/01.md)
    - [Composite identifiers](/domain/06/02.md)
    - [Composite identifiers with @EmbeddedId](/domain/06/03.md)
    - [Composite identifiers with @IdClass](/domain/06/04.md)
    - [Composite identifiers with associations](/domain/06/05.md)
    - [Generated identifier values](/domain/06/06.md)
    - [Interpreting AUTO](/domain/06/07.md)
    - [Using sequences](/domain/06/08.md)
    - [Using IDENTITY columns](/domain/06/09.md)
    - [Using identifier table](/domain/06/10.md)
    - [Using UUID generation](/domain/06/11.md)
    - [Optimizers](/domain/06/12.md)
    - [Using @GenericGenerator](/domain/06/13.md)
    - [Derived Identifiers](/domain/06/14.md)
