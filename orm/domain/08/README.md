- [Domain Model](/orm/domain/README.md)
  - [Collections](/orm/domain/08/README.md)
    - [Collections as a value type](/orm/domain/08/01.md)
    - [Collections of value types](/orm/domain/08/02.md)
    - [Collections of entities](/orm/domain/08/03.md)
    - [Bags](/orm/domain/08/04.md)
    - [Ordered Lists](/orm/domain/08/05.md)
    - [Sets](/orm/domain/08/06.md)


persistent collections must be declared as an interface type. The actual interface might be java.util.Collection, java.util.List, java.util.Set, java.util.Map, java.util.SortedSet, java.util.SortedMap or even other object types (meaning you will have to write an implementation of org.hibernate.usertype.UserCollectionType).


The persistent collections injected by Hibernate behave like ArrayList, HashSet, TreeSet, HashMap or TreeMap, depending on the interface type.


