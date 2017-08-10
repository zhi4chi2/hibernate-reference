JPA 接口及 Hibernate 实现
- javax.persistence.EntityManagerFactory - org.hibernate.jpa.internal.EntityManagerFactoryImpl, 内部使用 org.hibernate.engine.spi.SessionFactoryImplementor 实现
- javax.persistence.EntityManager - org.hibernate.jpa.internal.EntityManagerImpl, 内部使用 org.hibernate.Session 实现
- javax.persistence.EntityTransaction - org.hibernate.jpa.internal.TransactionImpl, 内部使用 org.hibernate.Transaction 实现


SessionFactoryImplementor 是 org.hibernate.SessionFactory 的子接口。


Hibernate 各接口的实现类：
- org.hibernate.SessionFactory - org.hibernate.internal.SessionFactoryImpl
- org.hibernate.Session - org.hibernate.internal.SessionImpl
- org.hibernate.Transaction - org.hibernate.engine.transaction.internal.TransactionImpl, 注意 Hibernate 5 没有 JdbcTransaction, JtaTransaction, CMTTransaction 类


SessionFactory 表示从 domain model 到 database 的 mapping ，是线程安全的。提供所有 Session 都可用的服务，比如 second level caches, connection pools, transaction system integrations


Session 包装了 java.sql.Connection ，也是 org.hibernate.Transaction 的工厂。


org.hibernate.Transaction 用于划分事务边界，是抽象的，隔离底层的 JDBC/JPA 等事务。
