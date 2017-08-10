persistent collections must be declared as an interface type. The actual interface might be java.util.Collection, java.util.List, java.util.Set, java.util.Map, java.util.SortedSet, java.util.SortedMap or even other object types (meaning you will have to write an implementation of org.hibernate.usertype.UserCollectionType).


The persistent collections injected by Hibernate behave like ArrayList, HashSet, TreeSet, HashMap or TreeMap, depending on the interface type.


- [Domain Model](/domain/README.md)
  - [Collections](/domain/08/README.md)
    - [Collections as a value type](/domain/08/01.md)
    - [Collections of value types](/domain/08/02.md)
    - [Collections of entities](/domain/08/03.md)
    - [Bags](/domain/08/04.md)
    - [Ordered Lists](/domain/08/05.md)
    - [Sets](/domain/08/06.md)
