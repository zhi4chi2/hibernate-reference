# many-to-many 需要关联表设置主键
```sql
create table a(id bigint not null primary key, a varchar(255));
create table b(id bigint not null primary key, b varchar(255));
create table a_b(a_id bigint not null references a(id), b_id bigint not null references b(id));
```


则不会生成 many-to-many ，而是生成两个 one-to-many/many-to-one 。


生成类：
- A
- B
- AB
- ABId


改为
```sql
drop table if exists a_b;
drop table if exists a;
drop table if exists b;

create table a(id bigint not null primary key, a varchar(255));
create table b(id bigint not null primary key, b varchar(255));
create table a_b(a_id bigint not null references a(id), b_id bigint not null references b(id), constraint uk_a_b unique(a_id, b_id));
```
都不行。


改为
```sql
drop table if exists a_b;
drop table if exists a;
drop table if exists b;

create table a(id bigint not null primary key, a varchar(255));
create table b(id bigint not null primary key, b varchar(255));
create table a_b(a_id bigint not null references a(id), b_id bigint not null references b(id), primary key(a_id, b_id));
```


这时会生成两个类，且正确设置 @ManyToMany
- A
- B


# many-to-many 不能改 property 名
```sql
drop table if exists t_a_b;
drop table if exists t_a;
drop table if exists t_b;

create table t_a(id bigint not null primary key, a varchar(255));
create table t_b(id bigint not null primary key, b varchar(255));
create table t_a_b(
  a_id bigint not null,
  b_id bigint not null,
  primary key(a_id, b_id),
  constraint t_a_b_a_id_fkey foreign key (a_id),
  constraint t_a_b_b_id_fkey foreign key (b_id)
);
```


默认生成的 TA 为
```java
     private Long id;
     private String a;
     private Set<TB> TBs = new HashSet<TB>(0);
```


如果希望更改属性名为 bs 。使用 src/main/resources/test.reveng.xml
```xml
<!DOCTYPE hibernate-reverse-engineering PUBLIC 
    "-//Hibernate/Hibernate Reverse Engineering DTD 3.0//EN"
    "http://hibernate.sourceforge.net/hibernate-reverse-engineering-3.0.dtd">
<hibernate-reverse-engineering>
  <table schema="public" name="t_a_b">
    <foreign-key constraint-name="t_a_b_a_id_fkey">
      <many-to-one exclude="true" />
      <set property="bs" />
    </foreign-key>
    <foreign-key constraint-name="t_a_b_b_id_fkey">
      <many-to-one exclude="true" />
      <set exclude="true" />
    </foreign-key>
  </table>
</hibernate-reverse-engineering>
```


但实际并不起作用，依然生成
```java
     private Long id;
     private String a;
     private Set<TB> TBs = new HashSet<TB>(0);
```


不过对 t_a_b_b_id_fkey 的 exclude 起作用了，在 TB 中不再生成 TAs


没有找到更改 many-to-many property 名的办法。


