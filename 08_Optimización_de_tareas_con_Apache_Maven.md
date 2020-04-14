# 8. Optimización de tareas con Apache Maven 12m

* Optimización de tareas con Apache Maven 7:21 
* Consejos y trucos 4:40 
* Contenido adicional 2

## Optimización de tareas con Apache Maven 7:21 

[Optimización de tareas con Apache Maven](pdfs/7.1_Optimización_de_tareas_con_Apache_Maven.pdf)

Optimizar tareas significa evitar errores, saber mecanismos para resolución de conflictos y hacer que los desarrolladores de un proyecto trabajen de una forma más productiva.

### ENTORNOS DE DESARROLLO OPTIMIZADOS EN E CLIPSE

* Configurar adecuadamente el mecanismo de publicación de cambios en el plugin WTP (Web server Tool Project) de Eclipse 

   Hay que tener cuidado con el plugin WTP al hacer las publicaciones de las aplicaciones para estar en ejecución, cuando trabajamos con resolución de otros proyectos en el mismo workspace en determinadas ocaciones puede existir el fallo de que no se llegue a publicar el cambio en el servidor de aplicaciones, para lo clual podemos usar el plugin filesync 
   
### TRABAJANDO CON PROYECTOS CONFIGURADOS CON PERFILES

* Activación de perfiles
   * .. por proyecto (Properties)
   * .. por workspace (en settings.xml)
   * .. en función Sistema Operativo
   * .. en función de la versión de JDK
   
* Filtrado de recursos
   * En tiempo de compilación/empaquetado
   * Maven Filters
   * Resolución de variables
   * En tiempo de ejecución
   * Spring Framework – Property Configurer
   * Spring Framework – Spring Active Profile  
   
El uso de perfiles en Maven es una practica habitual pero no es la mejor opción. Lo ideal que cuando generamos una aplicación y la empaquetamos, esa aplicación sea invariante de un entorno a otro de manera de que si compilas la aplicación War para el entorno local y luego la despliegas en el entorno de Desarrollo, Pruebas y Producción funcione, para acotar los posibles fallos.

Pero si se van a utilizar perfiles de configuración Maven para cada uno de los entornos se pueden usar los filtros o el plugin Maven Source 

## Consejos y trucos 4:40 

[Consejos y trucos](pdfs/7.2_Recopilacion_consejos_y_trucos_.pdf)

### RECOPILACIÓN DE CONSEJOS Y TRUCOS

* Ten presente el ciclo de vida de Maven y sus fases
* Refresca en tu IDE si has compilado por detrás
* Cuidado al trabajar con dos ramas de un mismo proyecto (RELEASE y SNAPSHOTs)
* Ten siempre presente la configuración del proxy
* No compartir en repositorios de código fuente configuraciones de settings.xml personales
* Forzado de actualización de SNAPSHOTs si se queda cacheado de forma errónea 
* Usa classiffiers identificativos si despliegas librerías estándar modificadas
* Fuerza la actualización de snapshots y regenera los índices de tu IDE si no cuentas con librerías que se hayan descargado correctamente
* Utiliza los fuentes de las librerías para depurar 

* Contenido adicional 2

[Optimización de tareas con Apache Maven](pdfs/7.1_Optimización_de_tareas_con_Apache_Maven.pdf)

[Consejos y trucos](pdfs/7.2_Recopilacion_consejos_y_trucos_.pdf)
