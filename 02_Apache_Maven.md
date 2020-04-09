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






## Instalación de librerías 4:18 

## Árbol de dependencias 6:18 

## Ejemplo práctico: Apache Maven 10:54 

## Contenido adicional 2
