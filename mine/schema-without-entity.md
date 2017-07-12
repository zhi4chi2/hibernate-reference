```java
package org.example.demo.hibernate;

import org.hibernate.MappingException;
import org.hibernate.dialect.Dialect;
import org.hibernate.dialect.PostgreSQL9Dialect;
import org.hibernate.engine.spi.Mapping;
import org.hibernate.id.factory.IdentifierGeneratorFactory;
import org.hibernate.id.factory.internal.DefaultIdentifierGeneratorFactory;
import org.hibernate.mapping.Column;
import org.hibernate.mapping.Table;
import org.hibernate.type.BasicTypeRegistry;
import org.hibernate.type.SingleColumnType;
import org.hibernate.type.Type;

public class Test {
    private Mapping mapping = new SimpleMapping();
    private Dialect dialect = new PostgreSQL9Dialect();
    private BasicTypeRegistry basicTypeRegistry = new BasicTypeRegistry();

    private static final String DEFAULT_CATALOG = null;
    private static final String DEFAULT_SCHEMA = "public";

    public void createSchema() {
        Table table = new Table("test");

        Column c = new Column("id");
        c.setNullable(false);
        c.setPrecision(10);
        c.setScale(0);
        c.setSqlType(getSqlType(dialect, basicTypeRegistry, "long", c));
        table.addColumn(c);

        c = new Column("a");
        c.setNullable(false);
        c.setPrecision(10);
        c.setScale(2);
        c.setSqlType(getSqlType(dialect, basicTypeRegistry, "big_decimal", c));
        table.addColumn(c);

        c = new Column("b");
        c.setNullable(false);
        c.setSqlType(getSqlType(dialect, basicTypeRegistry, "timestamp", c));
        table.addColumn(c);

        c = new Column("c");
        c.setNullable(false);
        c.setLength(255);
        c.setSqlType(getSqlType(dialect, basicTypeRegistry, "string", c));
        table.addColumn(c);

        String sql = table.sqlCreateString(dialect, mapping, DEFAULT_CATALOG, DEFAULT_SCHEMA);
        // create table public.test (id int8 not null, a numeric(10, 2) not null, b timestamp not null, c varchar(255) not null)
        System.out.println(sql);
    }

    public static void main(String[] args) throws Exception {
        new Test().createSchema();
    }

    public String getSqlType(Dialect dialect, BasicTypeRegistry basicTypeRegistry, String key, Column c) {
        return dialect.getTypeName(((SingleColumnType<?>) basicTypeRegistry.getRegisteredType(key)).sqlType(),
                c.getLength(), c.getPrecision(), c.getScale());
    }

    private static class SimpleMapping implements Mapping {
        @Override
        public IdentifierGeneratorFactory getIdentifierGeneratorFactory() {
            return new DefaultIdentifierGeneratorFactory();
        }

        @Override
        public Type getIdentifierType(String className) throws MappingException {
            return null;
        }

        @Override
        public String getIdentifierPropertyName(String className) throws MappingException {
            return null;
        }

        @Override
        public Type getReferencedPropertyType(String className, String propertyName) throws MappingException {
            return null;
        }
    }
}
```
