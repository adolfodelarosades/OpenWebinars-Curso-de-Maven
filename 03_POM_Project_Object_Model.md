# 3. POM (Project Object Model) 80m

* Introducción a POM (Project Object Model) 3:49 
* Sintaxis del POM (Project Object Model) 9:45 
* Declaración de dependencias 14:40 
* Dependency plugins 9:52 
* Definición de repositorios 12:13 
* Definición del flujo de construcción y fases del ciclo de vida 3:27 
* Plugins Maven mas conocidos 8:16 
* Uso de perfiles de configuración 8:52 
* Ejemplo práctico: POM (Project Object Model) 9:43 
* Contenido adicional  8


## Introducción a POM (Project Object Model) 3:49 

[Introducción a POM](pdfs/3.1_Introduccion_a_POM_.pdf)

Los ficheros POM son los que aglutinan toda la configuración y declaración de ejecuciones de Maven.
Desde definición de proyectos Maven, dependencias, flujos de construcción, etc.

Existe una analogía entre los ficheros `pom.xml` de **Apache Maven** y los `Makefile` de **GNU Make** o los `build.xml` de **Apache Ant**. Cada uno de estos tres ficheros ofrecen información de configuración que es usada por cada herramienta respectiva para construir el empaquetado binario (compilados) a partir del código fuente.

Maven casi siempre es usado en proyectos Java, pero eso no quiere decir que no esté preparado para ser usado en otros lenguajes como C# o C.

Maven va mucho más allá de una mera herramienta de construcción y empaquetado de aplicaciones, permite gestionar todo el ciclo de vida de un proyecto contemplando ámbitos como CI/CD (integración contínua y entrega contínua), testing, control de calidad, etc.

## Sintaxis del POM (Project Object Model) 9:45 

[Sintaxis del POM](pdfs/3.2_Sintaxis_del_POM_.pdf)

Veamos como ejemplo el POM más sencillo que se puede declarar:

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>
  <groupId>net.openwebinars</groupId>
  <artifactId>simplest-project</artifactId>
  <version>1</version>
</project>
Si ejecutamos el comando $> mvn help:effective-pom obtendremos el POM efectivo que en realidad hemos definido teniendo en cuenta, del mismo modo que en la programación orientada a objetos, la configuración heredada del super POM:

<?xml version="1.0"?>
<project xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd" xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
  <modelVersion>4.0.0</modelVersion>
  <groupId>net.openwebinars</groupId>
  <artifactId>simplest-project</artifactId>
  <version>1</version>
  <repositories>
    <repository>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
      <id>central</id>
      <name>Central Repository</name>
      <url>https://repo.maven.apache.org/maven2</url>
    </repository>
  </repositories>
  <pluginRepositories>
    <pluginRepository>
      <releases>
        <updatePolicy>never</updatePolicy>
      </releases>
      <snapshots>
        <enabled>false</enabled>
      </snapshots>
      <id>central</id>
      <name>Central Repository</name>
      <url>https://repo.maven.apache.org/maven2</url>
    </pluginRepository>
  </pluginRepositories>
  <build>
    <sourceDirectory>C:\dev\workspace\simplest-project\src\main\java</sourceDirectory>
    <scriptSourceDirectory>C:\dev\workspace\simplest-project\src\main\scripts</scriptSourceDirectory>
    <testSourceDirectory>C:\dev\workspace\simplest-project\src\test\java</testSourceDirectory>
    <outputDirectory>C:\dev\workspace\simplest-project\target\classes</outputDirectory>
    <testOutputDirectory>C:\dev\workspace\simplest-project\target\test-classes</testOutputDirectory>
    <resources>
      <resource>
        <directory>C:\dev\workspace\simplest-project\src\main\resources</directory>
      </resource>
    </resources>
    <testResources>
      <testResource>
        <directory>C:\dev\workspace\simplest-project\src\test\resources</directory>
      </testResource>
    </testResources>
    <directory>C:\dev\workspace\simplest-project\target</directory>
    <finalName>simplest-project-1</finalName>
    <pluginManagement>
      <plugins>
        <plugin>
          <artifactId>maven-antrun-plugin</artifactId>
          <version>1.3</version>
        </plugin>
        <plugin>
          <artifactId>maven-assembly-plugin</artifactId>
          <version>2.2-beta-5</version>
        </plugin>
        <plugin>
          <artifactId>maven-dependency-plugin</artifactId>
          <version>2.8</version>
        </plugin>
        <plugin>
          <artifactId>maven-release-plugin</artifactId>
          <version>2.3.2</version>
        </plugin>
      </plugins>
    </pluginManagement>
    <plugins>
      <plugin>
        <artifactId>maven-clean-plugin</artifactId>
        <version>2.5</version>
        <executions>
          <execution>
            <id>default-clean</id>
            <phase>clean</phase>
            <goals>
              <goal>clean</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-resources-plugin</artifactId>
        <version>2.6</version>
        <executions>
          <execution>
            <id>default-testResources</id>
            <phase>process-test-resources</phase>
            <goals>
              <goal>testResources</goal>
            </goals>
          </execution>
          <execution>
            <id>default-resources</id>
            <phase>process-resources</phase>
            <goals>
              <goal>resources</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-jar-plugin</artifactId>
        <version>2.4</version>
        <executions>
          <execution>
            <id>default-jar</id>
            <phase>package</phase>
            <goals>
              <goal>jar</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.1</version>
        <executions>
          <execution>
            <id>default-compile</id>
            <phase>compile</phase>
            <goals>
              <goal>compile</goal>
            </goals>
          </execution>
          <execution>
            <id>default-testCompile</id>
            <phase>test-compile</phase>
            <goals>
              <goal>testCompile</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-surefire-plugin</artifactId>
        <version>2.12.4</version>
        <executions>
          <execution>
            <id>default-test</id>
            <phase>test</phase>
            <goals>
              <goal>test</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-install-plugin</artifactId>
        <version>2.4</version>
        <executions>
          <execution>
            <id>default-install</id>
            <phase>install</phase>
            <goals>
              <goal>install</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-deploy-plugin</artifactId>
        <version>2.7</version>
        <executions>
          <execution>
            <id>default-deploy</id>
            <phase>deploy</phase>
            <goals>
              <goal>deploy</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
      <plugin>
        <artifactId>maven-site-plugin</artifactId>
        <version>3.3</version>
        <executions>
          <execution>
            <id>default-site</id>
            <phase>site</phase>
            <goals>
              <goal>site</goal>
            </goals>
            <configuration>
              <outputDirectory>C:\dev\workspace\simplest-project\target\site</outputDirectory>
              <reportPlugins>
                <reportPlugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-project-info-reports-plugin</artifactId>
                </reportPlugin>
              </reportPlugins>
            </configuration>
          </execution>
          <execution>
            <id>default-deploy</id>
            <phase>site-deploy</phase>
            <goals>
              <goal>deploy</goal>
            </goals>
            <configuration>
              <outputDirectory>C:\dev\workspace\simplest-project\target\site</outputDirectory>
              <reportPlugins>
                <reportPlugin>
                  <groupId>org.apache.maven.plugins</groupId>
                  <artifactId>maven-project-info-reports-plugin</artifactId>
                </reportPlugin>
              </reportPlugins>
            </configuration>
          </execution>
        </executions>
        <configuration>
          <outputDirectory>C:\dev\workspace\simplest-project\target\site</outputDirectory>
          <reportPlugins>
            <reportPlugin>
              <groupId>org.apache.maven.plugins</groupId>
              <artifactId>maven-project-info-reports-plugin</artifactId>
            </reportPlugin>
          </reportPlugins>
        </configuration>
      </plugin>
    </plugins>
  </build>
  <reporting>
    <outputDirectory>C:\dev\workspace\simplest-project\target\site</outputDirectory>
  </reporting>
</project>
Evidentemente, y continuando utilizando la analogía de la programación orientada a objetos, esta configuración heredada puede ser sobreescrita y ampliada.

Estructura del POM
Cuatro categorías de descripción y configuración:

Información general del proyecto: Nombre del proyecto, URL, lista de desarrolladores y contribuyentes
Configuración de construcción: Customización de la configuración manual de construcción definida por defecto
Configuración de entornos a través de la definición de perfiles de config, por entorno, etc.
Dependencias entre proyectos y librerías

## Declaración de dependencias 14:40 

## Dependency plugins 9:52 

## Definición de repositorios 12:13 

## Definición del flujo de construcción y fases del ciclo de vida 3:27 

## Plugins Maven mas conocidos 8:16 

## Uso de perfiles de configuración 8:52 

## Ejemplo práctico: POM (Project Object Model) 9:43 

## Contenido adicional  8
