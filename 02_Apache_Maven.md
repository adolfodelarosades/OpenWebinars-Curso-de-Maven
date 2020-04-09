# 2. Apache Maven 47m

* Introducción a Apache Maven 6:15 
* Instalación y configuración 10:04 
* Compilación y empaquetado 9:46 
* Instalación de librerías 4:18 
* Árbol de dependencias 6:18 
* Ejemplo práctico: Apache Maven 10:54 
* Contenido adicional 2

## Introducción a Apache Maven 6:15 

[Introducción a Apache Maven](pdfs/2.1_Introudcción_a_Apache_Maven.pdf)

## Instalación y configuración 10:04 

[Instalación y configuración](pdfs/2.2_Instalacion.pdf)

[Pagina oficial de Maven](https://maven.apache.org/)

### Intalar Maven en un Mac desde la consola

[Video](https://www.youtube.com/watch?v=j0OnSAP-KtU&vl=es)

[cmder](https://cmder.net/)

* Descargar Maven de la página oficial 

   Descargaremos el archivo `Binary tar.gz archive`:

   <img src="images/2-maven-download.png">
   
* Una vez descargado el archivo lo descomprimimos

   <img src="images/2-maven-download-2.png">
   
   <img src="images/2-maven-download-3.png">
   
   Lo más habitual será trabajar con la carpeta `conf` y con el archivo `settings.xml`, que es el archivo de configuración global de Maven.
   
   <img src="images/2-maven-download-4.png">
   
* Vamos a mover nuestro archivo Maven al directorio `Applications`   

   ```
   mini-de-adolfo:~ adolfodelarosa$ cd Downloads/
   mini-de-adolfo:Downloads adolfodelarosa$ mv apache-maven-3.6.3 /Applications/
   mini-de-adolfo:Downloads adolfodelarosa$ cd /Applications/
   mini-de-adolfo:Applications adolfodelarosa$ cd apache-maven-3.6.3/
   mini-de-adolfo:apache-maven-3.6.3 adolfodelarosa$ pwd
   /Applications/apache-maven-3.6.3
   
   mini-de-adolfo:apache-maven-3.6.3 adolfodelarosa$ cd /Users/adolfodelarosa/
   mini-de-adolfo:~ adolfodelarosa$ mini-de-adolfo:~ adolfodelarosa$ ls -a
   .				.vagrant.d
   ..				.viminfo
   .CFUserTextEncoding		.vscode
   .DS_Store			Adolfo2020
   .Trash				AndroidStudioProjects
   .android			Applications
   .angular-config.json		Desktop
   .bash_history			Documents
   .bash_profile			Downloads
   
   mini-de-adolfo:~ adolfodelarosa$ open -e .bash_profile   
   ```
* El ultimo comando abre el archivo `.bash_profile` en el editor por default, insertamos el siguiente código:

   ```sh
   export M2_HOME=/Applications/apache-maven-3.6.3
   export PATH=$PATH:$M2_HOME/bin
   ```
  
  Salvamos el archivo
  
* Una vez hecho lo anterior, pulsamos el siguiente comando:

   ```sh
   mini-de-adolfo:~ adolfodelarosa$ source .bash_profile
   ```
* Y ya podemos ejecutar Maven:

   ```sh   
   mini-de-adolfo:~ adolfodelarosa$ mvn -version
   Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f)
   Maven home: /Applications/apache-maven-3.6.3
   Java version: 14, vendor: Oracle Corporation, runtime: /Library/Java/JavaVirtualMachines/jdk-14.jdk/Contents/Home
   Default locale: es_ES, platform encoding: UTF-8
   OS name: "mac os x", version: "10.15", arch: "x86_64", family: "mac"
   mini-de-adolfo:~ adolfodelarosa$ 
   ```
### Intalar Maven en un Mac en Eclipse 

Maven ya viene instalado por defecto en Eclipse, pero si lo preferimos podemos poner la versión instalada desde la consola para que sea la que use Eclipse ya que ofrece la ventaja de saber exactamente donde esta contenida la instalación de Maven.

* Para hacer esto vamos a *Preferencias/Maven/Instalación* y a añadimos nuestra versión:

   <img src="images/2-maven-eclipse.png">

* Para comprobar que todo va bien podemos descargar el siguiente proyecto Maven y abrirlo desde Eclipse.

   https://github.com/jitpack/maven-modular

* Importamos un proyecto Maven

   <img src="images/2-eclipse-import.png">

   <img src="images/2-eclipse-proyecto-maven.png">

### Visualizarlo desde la consola

* Desde la consola podemos ubicarnos donde se encuentra el proyecto:

   `cd /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/maven-modular-master`

* Podemos ver la estructura del proyecto

   ```sh
   mini-de-adolfo:maven-modular-master adolfodelarosa$ ls
   LICENSE		README.md	module1		module2		pom.xml
   
   mini-de-adolfo:maven-modular-master adolfodelarosa$ cd module1
   mini-de-adolfo:module1 adolfodelarosa$ ls
   pom.xml	src	target
   
   mini-de-adolfo:module1 adolfodelarosa$ cd ..
   mini-de-adolfo:maven-modular-master adolfodelarosa$ cd module2
   mini-de-adolfo:module2 adolfodelarosa$ ls
   pom.xml	src	target
   mini-de-adolfo:module2 adolfodelarosa$ 
   ```
   
   Es un proyecto Maven con dos modulos y su archivo `pom.xml` y a su vez cada modulo es otro proyecto Maven con su propio archivo `pom.xml`.

* Si estando en el proyecto principal pulsamos `mvn`, identifica el contenido:

   <img src="images/2-maven-mvn.png">

   Nos presenta errores por que no dimos ningún comando Maven, 
   
* Si pulsamos `mvn compile` podemos ver como nos compila el proyecto:

   <img src="images/2-maven-mvn-2.png">

## Compilación y empaquetado 9:46

Para empezar con los comandos desde la consola nos descargamos el siguiente repositirio:

[Apache Commons IO](https://github.com/apache/commons-io)

En nuestra consola nos vamos a la carpeta donde hemos descargado el proyecto:

```sh
cd /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master

mini-de-adolfo:commons-io-master adolfodelarosa$ pwd
/Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master
mini-de-adolfo:commons-io-master adolfodelarosa$ 
```

Podemos apreciar el contenido de este proyecto

<img src="images/2-commons-io.png">

### Comando `mvn compile`

Crea el directorio `target` con los `.class` asociados a los fuentes que hay en la carpeta `src`

```sh
mini-de-adolfo:commons-io-master adolfodelarosa$ mvn compile
[INFO] Scanning for projects...
Downloading from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-parent/50/commons-parent-50.pom
Downloaded from central: https://repo.maven.apache.org/maven2/org/apache/commons/commons-parent/50/commons-parent-50.pom (76 kB at 66 kB/s)
[INFO] 
[INFO] -----------------------< commons-io:commons-io >------------------------
[INFO] Building Apache Commons IO 2.7-SNAPSHOT
[INFO] --------------------------------[ jar ]---------------------------------

...

[INFO] /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/src/main/java/org/apache/commons/io/IOExceptionList.java: Recompile with -Xlint:unchecked for details.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  20.019 s
[INFO] Finished at: 2020-04-09T19:04:36+02:00
[INFO] ------------------------------------------------------------------------
mini-de-adolfo:commons-io-master adolfodelarosa$ 
```

<img src="images/2-mvn-target.png">

<img src="images/2-mvn-compile.png">

Podemos apreciar como se ha generado la carpeta `target` y dentro de ella se han creado todos los archivos `.class`.

### Comando `mvn clean`

Borra todo el contenido del directorio `target` que es donde se almacenan todos los compilados del proyecto.


### Comando `mvn clean`

Si pulsamos el comando `mvn clean`:

<img src="images/2-mvn-clean-2.png>

Vemos como la carpeta `target` se elimina junto con todo su contenido.

<img src="images/2-commons-io-2.png>
          
### Comando `mvn clean package`          

Este comando nos permite eliminar lo ya compilado, para volverlo a compilar pero ademas empaquetarlo.

```sh
192:commons-io-master adolfodelarosa$ mvn clean package

... 

[INFO] Skipping because packaging 'jar' is not pom.
[INFO] 
[INFO] --- maven-jar-plugin:3.2.0:test-jar (default) @ commons-io ---
[INFO] Building jar: /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/target/commons-io-2.7-SNAPSHOT-tests.jar
[INFO] 
[INFO] --- maven-source-plugin:3.2.0:jar-no-fork (create-source-jar) @ commons-io ---
[INFO] Building jar: /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/target/commons-io-2.7-SNAPSHOT-sources.jar
[INFO] 
[INFO] --- maven-source-plugin:3.2.0:test-jar-no-fork (create-source-jar) @ commons-io ---
[INFO] Building jar: /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/target/commons-io-2.7-SNAPSHOT-test-sources.jar
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  05:03 min
[INFO] Finished at: 2020-04-09T20:58:08+02:00
[INFO] ------------------------------------------------------------------------
192:commons-io-master adolfodelarosa$
```

Cuando finaliza se crea la carpeta `target` con todos los archivos `.class` pero ademas de esto se crean los archivos `.jar`:

```
commons-io-2.7-SNAPSHOT-sources.jar
commons-io-2.7-SNAPSHOT-test-sources.jar
commons-io-2.7-SNAPSHOT-tests.jar
commons-io-2.7-SNAPSHOT.jar
```

Nosotros podriamos distribuir el archivo `commons-io-2.7-SNAPSHOT-sources.jar` para que pueda ser incluido en otros proyectos y pueda ser utilizado todo el código desarrollado en esa libreria.

Ademas de este jar genera otro para los `sources`, otro de `test`y uno de `test-sources`.

### Respositorio local

Maven tiene un repositorio local por default donde va recolectando todas las dependencias y librerias que va necesitando y que descarga de repositorios remotos y las coloca en el repositorio local para optimizar la velocidad de compilación.

Este repositorio local por defaul esta ubicado en:

`/Users/adolfodelarosa/.m2/repository`

Para este proyecto si abrimos el archivo `pom.xml` tenemos:

```
<groupId>commons-io</groupId>
<artifactId>commons-io</artifactId>
<version>2.7-SNAPSHOT</version>
```

Tanto el `groupId` como `artifactId` tienen como valor `commons-io`, por lo que en el repositorio local debemos encontrar esta dependencia.

**Explicación de cómo se crea el respositorio local:**

* Por defecto Maven, si no le decimos nada, utilizará como ruta por defecto del repositorio local `{tu carpeta de usuario}/.m2/repository`

* En la primera ejecución de Maven si no existe dicho directorio lo creará

* Si por un casual queremos customizar esta ruta por el motivo que fuera, porque queremos diferenciar el repositorio local de un cliente a otro, por ejemplo: simplemente editaríamos la propiedad `localRepository` del fichero de configuración `%M2_HOME%/conf/settings.xml`

* Cuando comiencen a descargarse dependencias o a instalarse proyectos en local se guardaran en dicho repositorio atendiendo al `{groupId}/{artifactId}/{version}`

* Hay que tener en cuenta que normalmente el {groupId} suele estar organizado de un modo similar a los paquetes de clases en Maven, usando el caracter .como separador, y dicho separador se usará para establecer la jerarquía en el repositorio.

Por ejemplo la siguiente librería *commons-services*:

* `groupId: net.openwebinars.samples`
* `artifactId: commons-services`
* `version: 1.0`

Al instalarse en nuestro repositorio se guardaría en:

* `%USER_HOME%/.m2/repository/net/openwebinars/samples/commons-services/1.0/commons-services-1.0.jar`

   * Es decir que el primer nivel corresponde al `groupId`.
   * El segundo nivel corresponde al `artifactId`.
   * Y el tercer nivel corresponde a la `version`.

### Cambiar el repositorio local por defecto

* Editamos el archivo `%M2_HOME%/conf/settings.xml` añadiendo la línea:

   `<localRepository> ${user.home}/.m2/repository2</localRepository>`

* Verificamos el contenido de `.m2` para ver que solo existe `repository`:

```sh
192:.m2 adolfodelarosa$ pwd
/Users/adolfodelarosa/.m2

192:.m2 adolfodelarosa$ ls
repository
```

* Compilemos nuvamente nuestro proyecto con: 

   ```sh
   192:commons-io-master adolfodelarosa$ mvn clean package

   ... 
   [INFO] Skipping because packaging 'jar' is not pom.
   [INFO] 
   [INFO] --- maven-jar-plugin:3.2.0:test-jar (default) @ commons-io ---
   [INFO] Building jar: /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/target/commons-io-2.7-SNAPSHOT-tests.jar
   [INFO] 
   [INFO] --- maven-source-plugin:3.2.0:jar-no-fork (create-source-jar) @ commons-io ---
   [INFO] Building jar: /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/target/commons-io-2.7-SNAPSHOT-sources.jar
   [INFO] 
   [INFO] --- maven-source-plugin:3.2.0:test-jar-no-fork (create-source-jar) @ commons-io ---
   [INFO] Building jar: /Users/adolfodelarosa/Documents/Udemy2020/Cursos/OW/Maven/downloads/commons-io-master/target/commons-io-2.7-SNAPSHOT-test-sources.jar
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  05:12 min
   [INFO] Finished at: 2020-04-09T22:39:14+02:00
   [INFO] ------------------------------------------------------------------------
   mini-de-adolfo:commons-io-master adolfodelarosa$ 
   ```

* Una vez que finaliza la compilación, podemos ver que en `.m2` ya tenemos el `repository2` que incluimos en la configuración:

   ```sh
   192:.m2 adolfodelarosa$ ls
   repository	repository2

   192:.m2 adolfodelarosa$ cd repository2
   192:repository2 adolfodelarosa$ ls
   antlr				commons-chain			commons-logging			net
   aopalliance			commons-cli			commons-validator		org
   avalon-framework		commons-codec			de				oro
   backport-util-concurrent	commons-collections		dom4j				sslext
   biz				commons-digester		javax				xerces
   classworlds			commons-httpclient		junit				xml-apis
   com				commons-io			log4j				xmlunit
   commons-beanutils		commons-lang			logkit
   192:repository2 adolfodelarosa$ 

   ```

   Todo lo que vaya necesitando lo mete dentro de este repositorio.

## Instalación de librerías 4:18 

## Árbol de dependencias 6:18 

## Ejemplo práctico: Apache Maven 10:54 

## Contenido adicional 2
