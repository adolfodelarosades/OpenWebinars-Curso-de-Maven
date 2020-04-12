# 5. Definición de proyectos jerárquicos 36m

* Proyectos Maven jerárquicos 10:25 
* Concepto de dependencias transitivas 2:43 
* Buenas prácticas, ventajas y desventajas 8:13 
* Ejemplo práctico: Creación de un proyecto multi-módulo 15:19 
* Contenido adicional 3

## Proyectos Maven jerárquicos 10:25 

[Proyectos Maven jerárquicos](pdfs/5.1_Proyectos_Maven_Jerárquicos_.pdf)

Existen proyectos en los cuales el nivel de jerarquias es realmente complejo.

### Proyecto Apache CXF https://cxf.apache.org (Servicios Web)

Para poder ver el código del proyecto Apache CXF lo podemos hacer en el repositorio:

`https://github.com/apache/cxf`

El proyecto es bastante complejo con un alto número de modulos con su correspondiente `pom.xml`. La librería principal es **core** la cual no contiene modulos es un simple jar. Y existen ramas intermedias como `integration`, `distribution`, etc.

Este proyecto podriamos descargarlo e importarlo desde Eclipse pero lo ideal sería trabajarlo por partes ya que todo completo tiene una cantidad muy alta de modulos que lo harian muy pesado trabajarlo completo.

El siguiente diagrama muestra un resumen de las librerias principales que tiene el proyecto:

<img src="images/5-cxf.png">

Destaca uno de los plugins `codegen-plugin` que permite ejecutar la orden `wild the to java`, en proyectos SOA que definen contratos `wildyets`,  si te facilitan el `wildyet` de un cliente al que te tienes que integrar, utilizamos el plugins `codegen-plugin` para generar el código Java asociado al esquema del contrato y lo puedes utilizar para montarte el cliente del servicio web. 

Este proyecto es muy extento por que tiene librerias para Servicios REST, SOA, etc. pero un claro ejemplo de un proyecto jerarquico muy complejo.

Vamos a importar el proyecto a Eclipse pero solo indicandole que nos importe solo los modulos **core** y **codegen-plugin**.






## Concepto de dependencias transitivas 2:43 

[Concepto de dependencias transitivas](pdfs/5.2_Concepto_de_dependencias_transitivas.pdf)

## Buenas prácticas, ventajas y desventajas 8:13 

[Buenas prácticas, ventajas y desventajas](pdfs/5.3_Buenas_prácticas_ventajas_y_desventajas.pdf)

## Ejemplo práctico: Creación de un proyecto multi-módulo 15:19 

## Contenido adicional 3

[Proyectos Maven jerárquicos](pdfs/5.1_Proyectos_Maven_Jerárquicos_.pdf)

[Concepto de dependencias transitivas](pdfs/5.2_Concepto_de_dependencias_transitivas.pdf)

[Buenas prácticas, ventajas y desventajas](pdfs/5.3_Buenas_prácticas_ventajas_y_desventajas.pdf)
