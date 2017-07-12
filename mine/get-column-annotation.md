```java
package org.example.demo.hibernate;

import java.util.Iterator;

import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.Id;
import javax.persistence.Table;

import org.hibernate.boot.Metadata;
import org.hibernate.boot.MetadataSources;
import org.hibernate.boot.registry.StandardServiceRegistryBuilder;
import org.hibernate.mapping.Column;
import org.hibernate.mapping.PersistentClass;
import org.hibernate.mapping.Property;
import org.hibernate.service.ServiceRegistry;

public class Test {
    public static void main(String[] args) {
        ServiceRegistry standardRegistry = new StandardServiceRegistryBuilder()
                .applySetting("hibernate.connection.url", "jdbc:p6spy:postgresql://localhost:5432/test")
                .applySetting("hibernate.connection.username", "postgres")
                .applySetting("hibernate.connection.password", "postgres")
                .applySetting("hibernate.hbm2ddl.auto", "create").build();
        Metadata metadata = new MetadataSources(standardRegistry).addAnnotatedClass(A.class).getMetadataBuilder()
                .build();

        PersistentClass pc = metadata.getEntityBinding("org.example.demo.hibernate.Test$A");
        String tableName = pc.getTable().getName();

        // tableName: t_a
        System.out.println("tableName: " + tableName);
        // id column: a_id
        System.out.println("id column: " + ((Column) pc.getIdentifierProperty().getColumnIterator().next()).getName());
        // columns: 
        //      a_a1
        //      a2
        System.out.println("columns: ");
        @SuppressWarnings("unchecked")
        Iterator<Property> i = pc.getPropertyIterator();
        for (; i.hasNext();) {
            Property p = (Property) i.next();
            if (p.getColumnIterator().hasNext()) {
                Column c = (Column) p.getColumnIterator().next();
                System.out.println("\t" + c.getName());
            }
        }
    }

    @Entity
    @Table(name = "t_a")
    public class A {
        @Id
        @GeneratedValue
        @javax.persistence.Column(name = "a_id")
        private Long id;
        @javax.persistence.Column(name = "a_a1")
        private String a1;
        String a2;
    }
}
```
