# 测试项目
pom.xml
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <parent>
    <groupId>org.example.demo</groupId>
    <artifactId>demo-parent</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <relativePath>../pom.xml</relativePath>
  </parent>

  <artifactId>demo-hibernate-tool</artifactId>
  <packaging>jar</packaging>

  <name>demo-hibernate-tool</name>

  <dependencies>
    <dependency>
      <groupId>org.hibernate</groupId>
      <artifactId>hibernate-tools</artifactId>
      <version>5.2.3.Final</version>
    </dependency>
    <dependency>
      <groupId>org.postgresql</groupId>
      <artifactId>postgresql</artifactId>
      <version>9.4.1212</version>
    </dependency>

    <dependency>
      <groupId>org.slf4j</groupId>
      <artifactId>slf4j-api</artifactId>
    </dependency>
    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
    </dependency>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```


build.xml
```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<project basedir="." default="reveng" name="demo-hibernate-tool">
	<property name="M2_REPO" value="F:/repo" />
	<property name="target" value="1.8" />
	<property name="source" value="1.8" />
	<path id="Maven Dependencies.libraryclasspath">
		<pathelement location="${M2_REPO}/org/hibernate/hibernate-tools/5.2.3.Final/hibernate-tools-5.2.3.Final.jar" />
		<pathelement location="${M2_REPO}/org/hibernate/hibernate-core/5.2.9.Final/hibernate-core-5.2.9.Final.jar" />
		<pathelement location="${M2_REPO}/org/jboss/logging/jboss-logging/3.3.0.Final/jboss-logging-3.3.0.Final.jar" />
		<pathelement location="${M2_REPO}/org/javassist/javassist/3.20.0-GA/javassist-3.20.0-GA.jar" />
		<pathelement location="${M2_REPO}/antlr/antlr/2.7.7/antlr-2.7.7.jar" />
		<pathelement location="${M2_REPO}/org/jboss/spec/javax/transaction/jboss-transaction-api_1.2_spec/1.0.1.Final/jboss-transaction-api_1.2_spec-1.0.1.Final.jar" />
		<pathelement location="${M2_REPO}/org/jboss/jandex/2.0.3.Final/jandex-2.0.3.Final.jar" />
		<pathelement location="${M2_REPO}/com/fasterxml/classmate/1.3.0/classmate-1.3.0.jar" />
		<pathelement location="${M2_REPO}/dom4j/dom4j/1.6.1/dom4j-1.6.1.jar" />
		<pathelement location="${M2_REPO}/org/hibernate/common/hibernate-commons-annotations/5.0.0.Final/hibernate-commons-annotations-5.0.0.Final.jar" />
		<pathelement location="${M2_REPO}/org/hibernate/javax/persistence/hibernate-jpa-2.1-api/1.0.0.Final/hibernate-jpa-2.1-api-1.0.0.Final.jar" />
		<pathelement location="${M2_REPO}/commons-logging/commons-logging/1.2/commons-logging-1.2.jar" />
		<pathelement location="${M2_REPO}/org/apache/ant/ant/1.10.1/ant-1.10.1.jar" />
		<pathelement location="${M2_REPO}/org/apache/ant/ant-launcher/1.10.1/ant-launcher-1.10.1.jar" />
		<pathelement location="${M2_REPO}/org/freemarker/freemarker/2.3.23/freemarker-2.3.23.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/jdt/org.eclipse.jdt.core/3.12.2/org.eclipse.jdt.core-3.12.2.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.resources/3.11.1/org.eclipse.core.resources-3.11.1.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.expressions/3.5.100/org.eclipse.core.expressions-3.5.100.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.runtime/3.12.0/org.eclipse.core.runtime-3.12.0.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.osgi/3.11.3/org.eclipse.osgi-3.11.3.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.equinox.common/3.8.0/org.eclipse.equinox.common-3.8.0.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.jobs/3.8.0/org.eclipse.core.jobs-3.8.0.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.equinox.registry/3.6.100/org.eclipse.equinox.registry-3.6.100.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.equinox.preferences/3.6.1/org.eclipse.equinox.preferences-3.6.1.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.contenttype/3.5.100/org.eclipse.core.contenttype-3.5.100.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.equinox.app/1.3.400/org.eclipse.equinox.app-1.3.400.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.filesystem/1.6.1/org.eclipse.core.filesystem-1.6.1.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.text/3.6.0/org.eclipse.text-3.6.0.jar" />
		<pathelement location="${M2_REPO}/org/eclipse/platform/org.eclipse.core.commands/3.8.1/org.eclipse.core.commands-3.8.1.jar" />
		<pathelement location="${M2_REPO}/commons-collections/commons-collections/3.2.2/commons-collections-3.2.2.jar" />
		<pathelement location="${M2_REPO}/org/postgresql/postgresql/9.4.1212/postgresql-9.4.1212.jar" />
		<pathelement location="${M2_REPO}/org/slf4j/slf4j-api/1.7.22/slf4j-api-1.7.22.jar" />
		<pathelement location="${M2_REPO}/ch/qos/logback/logback-classic/1.1.9/logback-classic-1.1.9.jar" />
		<pathelement location="${M2_REPO}/ch/qos/logback/logback-core/1.1.9/logback-core-1.1.9.jar" />
		<pathelement location="${M2_REPO}/junit/junit/4.12/junit-4.12.jar" />
		<pathelement location="${M2_REPO}/org/hamcrest/hamcrest-core/1.3/hamcrest-core-1.3.jar" />
	</path>

	<taskdef name="hibernatetool" classname="org.hibernate.tool.ant.HibernateToolTask" classpathref="Maven Dependencies.libraryclasspath" />

	<target name="reveng">
		<hibernatetool destdir="generate" templatepath="${basedir}/template">
			<classpath>
				<path location="target/classes" />
			</classpath>
			<jdbcconfiguration configurationfile="src/main/resources/hibernate.cfg.xml" detectoptimisticlock="false" detectmanytomany="true" revengfile="src/main/resources/test.reveng.xml" reversestrategy="org.example.demo.hibernate.tools.ReverseEngineering" packagename="org.example.demo.hibernate.bo" />
			<hbm2java jdk5="true" ejb3="true" />
			<hbm2cfgxml />
		</hibernatetool>
	</target>

	<target name="genhbm">
		<hibernatetool destdir="generate">
			<classpath>
				<path location="target/classes" />
			</classpath>
			<configuration configurationfile="src/main/resources/hibernate.cfg.xml" />
			<hbm2hbmxml />
		</hibernatetool>
	</target>
</project>
```


src/main/resources/hibernate.cfg.xml
```xml
<?xml version='1.0' encoding='utf-8'?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
  <session-factory>
    <property name="connection.url">jdbc:postgresql://localhost:5432/test</property>
    <property name="connection.username">postgres</property>
    <property name="connection.password">postgres</property>
  </session-factory>
</hibernate-configuration>
```


src/main/resources/test.reveng.xml
```xml
<!DOCTYPE hibernate-reverse-engineering PUBLIC 
    "-//Hibernate/Hibernate Reverse Engineering DTD 3.0//EN"
    "http://hibernate.sourceforge.net/hibernate-reverse-engineering-3.0.dtd">
<hibernate-reverse-engineering>
</hibernate-reverse-engineering>
```


```java
package org.example.demo.hibernate.tools;

import org.hibernate.cfg.reveng.DelegatingReverseEngineeringStrategy;
import org.hibernate.cfg.reveng.ReverseEngineeringStrategy;
import org.hibernate.cfg.reveng.TableIdentifier;

public class ReverseEngineering extends DelegatingReverseEngineeringStrategy {
    public ReverseEngineering(ReverseEngineeringStrategy delegate) {
        super(delegate);
    }

    @Override
    public String getTableIdentifierStrategyName(TableIdentifier tableIdentifier) {
        return "increment";
    }

    public String tableToClassName(TableIdentifier tableIdentifier) {
        String prefix = "tb_";
        if (tableIdentifier.getName().toLowerCase().startsWith(prefix)) {
            String className = super.tableToClassName(tableIdentifier);
            return getClassName(className, prefix);
        } else {
            return super.tableToClassName(tableIdentifier);
        }
    }

    private static String getClassName(String className, String prefix) {
        int i = className.lastIndexOf('.');
        if (i == -1) {
            return className.substring(prefix.length() - 1);
        }
        String packagee = className.substring(0, i + 1);
        String clazz = className.substring(i + 1);
        if (clazz.toLowerCase().startsWith(prefix.substring(0, prefix.length() - 1).toLowerCase())) {
            // 去掉前缀，没有 _ ，所以只需要去掉 prefix.length()-1 个字符即可
            clazz = className.substring(i + prefix.length());
        }
        return packagee + clazz;
    }
}
```


## bug
- 运行 build.xml 时不使用配置的 src/main/resources/logback.xml 。之前的版本 hibernate-tools-4.3.1.Final 是可以用 src/main/resources/log4j.xml 的。


# 目录
- [Hibernate Tools](/tools/README.md)
