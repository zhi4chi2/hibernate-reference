Hibernate legacy(4.3.11) 只有
- update
- create - 先 drop 再 create
- create-drop - 在 SessionFactory shutdown 时 drop schema
- validate


且 4.3.11 就没有 org.hibernate.tool.schema.Action 这个类。


JPA 只有
- none
- create - Hibernate 新使用 create-only 对应此项
- drop - Hibernate 新使用 drop 对应此项
- drop-and-create - 与 Hibernate 原有的 create 含义一致

