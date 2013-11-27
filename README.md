Guia Básica de Selenium
============

### Descripción
[Selenium](http://www.seleniumhq.org/ "Selenium") es un conjunto de herramientas cuyo fin es ser un automatizador de navegador, generando pruebas funcionales en aplicaciones Web en diversos lenguajes como java, python, javascript, etc.

Selenium está dividida en 4 proyectos:
* [Selenium IDE](http://docs.seleniumhq.org/projects/ide/): Es un plugin para la aplicación Firefox, con el cual podemos capturar y ejecutar un conjunto de acciones (o pruebas) dentro del navegador, con opción de generar scripts para el almacenamiento en disco y/o modificación manual.
  * los scripts son un conjunto de instrucciones o pasos que pueden ser exportadas en distintos formatos como HTML, Java, etc.
  * La desventaja de usar unicamente Selenium IDE es que se está limitado a sólo poder ejecutarse en Firefox.
  * Existe una alternativa llamada [SeleniumBuilder](http://sebuilder.github.io/se-builder/) la cual ofrece algunas funcionalidades extras o mas avanzadas.
* [Selenium Remote Control (Selenium RC)](http://docs.seleniumhq.org/projects/remote-control/): Es un servidor RESTful que ejecuta instrucciones vía http y las ejecuta en el navegador que se le indique.
  * Se puedenutilizar los scripts generados por Selenium IDE, los cuales deben de ser interpretados por una [librería cliente](https://github.com/search?q=selenium+rc&type=Repositories&ref=searchresults) que le envía las instrucciones a SeleniumRC
* [Selenium WebDriver](http://docs.seleniumhq.org/projects/webdriver/): Es una interface para el control del navegador, la cual ya está implementado para los navegadores más comunes.
* [Selenium Grid](http://docs.seleniumhq.org/projects/webdriver/): Permite ejecutar en paralelo varios Selenium RC para realizar pruebas de concurrencia.

Puede ser encontrada más información en los siguientes enlaces:
 * [http://www.seleniumhq.org/docs/](http://www.seleniumhq.org/docs/)
 * [http://testingfuncional.wordpress.com/2012/12/30/trucos-de-selenium-ide-intro-recording-waiting/](http://testingfuncional.wordpress.com/2012/12/30/trucos-de-selenium-ide-intro-recording-waiting/)
 * [http://seleniumtutorials.com/2013/02/04/selenium/selenium-ide-tutorial/](http://seleniumtutorials.com/2013/02/04/selenium/selenium-ide-tutorial/)
 * [http://www.codediesel.com/php/selenium-ide-tutorial-part-1/](http://www.codediesel.com/php/selenium-ide-tutorial-part-1/)
 * [http://www.programandoconcafe.com/2011/10/selenium-herramienta-para-automatizar.html](http://www.programandoconcafe.com/2011/10/selenium-herramienta-para-automatizar.html)
 * [http://www.juntadeandalucia.es/servicios/madeja/contenido/recurso/381](http://www.juntadeandalucia.es/servicios/madeja/contenido/recurso/381)

### Script
Los scripts o instrucciones le indican a Selenium qué acciones realizar en el navegador, como pueden ser ir a una URL, esperar a que cargue la página, escribir sobre cierto campo, dar clic a un boton, esperar/comprobar cierto texto dentro de la página.
Un Script puede ser representado por un archivo físico, una suite de scripts representa varios scripts físicos. Al terminar de ejecutarse el script de una prueba puede ser que sea exitosa o fallida, en este caso se regresara el detalle del error y la instrucción del script donde ocurrió.

### Instrucción
Cada instrucción o paso tiene 3 propiedades:
 * Commando
 * Objetivo (opcional dependiendo del comando) donde se ejecutara el comando, este puede ser localizado por:
  * ID
  * nombre
  * CSS
  * DOM
  * [XPATH](http://www.w3.org/TR/xpath/) este es mas recomendable cuando las pruebas son muy dinamicas, ya que es un lenguaje robusto para localizar elementos dentro de una estructura XML.
 * Valor (opcional dependiendo del comando) esperado despues de ejecutar el comando

Una instrucción fallará cuando el comando indicado no exista, el objetivo no sea encontrado o el valor esperado es diferente

### Ventajas y desventajas
Las ventajas de utilizar Selenium son:
 * Desarrollo guiado por pruebas, o Test-driven development (TDD).
 * Definir conjunto de pruebas que cubran la mayoría de funciones del sistema, que puedan ser repetidas la cantidad de veces que sea, siguiendo los mismos pasos, evitando trabajo manual o susceptible a errores.
 * Al realizar un cambio al sistema, se pueden ejecutar las pruebas para comprobar los impactos contemplados y no contemplados.
 * Realizar las mismas pruebas en todos los navegadores compatibles.
 * Realizar la misma prueba con distintos clientes al mismo tiempo.
 * Recopilar evidencias físicas (logs, resultados, capturas de pantalla).
 * Evitar cosas como “eso ya lo habia probado”.
 * Minimizar tiempos en pruebas de funcionalidad para invertir en otro tipo de pruebas manuales como usabilidad.
Etc.

Desventajas:
 * Llegará un momento en el que realizar los Scripts es más lento que ejecutarlos manualmente.
 * Las pruebas llegarán a ser demasiado complejas para realizarse fácilmente en Selenium.
 * Selenium no permite reutilizar, por ejemplo parametrizar una prueba.
  * esto se puede realizar por medio de una librería cliente pero es más complejo, ya que se requiere realizar la programación necesaria.
 * No existe alguna herramienta que permita organizar las distintas etapas de las pruebas a un sistema.

### Como trabaja Selenium RC
![Arquitectura](http://www.seleniumhq.org/docs/_images/chapt5_img01_Architecture_Diagram_Simple.png)

La imagen muestra la arquitectura basica, donde nuestros scripts por medio de la libreria cliente son enviados a Selenium RC y este lo envia al navegador indicado, lo ejecuta y regresa el resultado.
####Instalación
Descargar desde la página oficial de Selenium RC el archivo JAR (requiere JAVA 1.5 o mayor) llamado selenium-server-standalone-<version-number>.jar y guardarlo en disco, no requiere algún directorio en especifico.

####Ejecución
En el directorio donde se encuentra el JAR ejecutar el siguiente comando para mantener el servidor en StandAlone:
java -jar selenium-server-standalone-<version-number>.jar, por defecto se inicia en el puerto 4444, y esta listo para recibir instrucciones por HTTP.
Para detener el servidor dar Ctrl + C

Para ejecutar directamente en el servidor un Script generado desde SeleniumIDE y exportado en formato HTML:
