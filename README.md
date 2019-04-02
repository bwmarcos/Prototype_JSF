# Prototype_JSF

### Como configurar novo Projeto JSF via Maven ArchType

- Criar um novo projeto Maven
  - maven-archetype-webapp
> Outra opção e criar o projeto em branco

- Definir Project Facet para:
  - Dynamic Web Module 3.1
  - Java 1.8
  - JavaServer Faces 2.3
### Extrutura dos arquivos
[![](https://github.com/bwmarcos/Prototype_JSF/blob/master/print.png)]

### Trocar o web.xml para 3.1 conforme abaixo:
```
<web-app
    xmlns="http://xmlns.jcp.org/xml/ns/javaee"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
         http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">
</web-app>
```
### Configurar o pom.xml conforme abaixo:
```  
<!-- Declaração das dependecias necessarias para JSF -->
<dependencies>
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
        <scope>provided</scope>
    </dependency>
    <dependency>
        <groupId>com.sun.faces</groupId>
        <artifactId>jsf-api</artifactId>
        <version>2.2.2</version>
    </dependency>
    <dependency>
        <groupId>com.sun.faces</groupId>
        <artifactId>jsf-impl</artifactId>
        <version>2.2.2</version>
    </dependency>
</dependencies>
<!-- Etapa de contrução do pacote -->
<build>
    <finalName>Prototype</finalName>
    <plugins>
        <plugin>
            <!-- declaracao do plugin Jetty para execução -->
            <groupId>org.eclipse.jetty</groupId>
            <artifactId>jetty-maven-plugin</artifactId>
            <version>9.3.14.v20161028</version>
            <configuration>
                <scanIntervalSeconds>10</scanIntervalSeconds>
            </configuration>
        </plugin>
    </plugins>
</build>
  ```
  ### Etapas de execução
 ```
 mvn clean 
 mvn package
 mvn jetty:run
 ```
 ### Executar a aplicação acesse o Link
* [localhost:8080](http://localhost:8080)
