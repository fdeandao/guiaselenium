Guia Básica de Selenium
============

[Selenium](http://www.seleniumhq.org/ "Selenium") es un conjunto de herramientas cuyo fin es ser un automatizador de navegador, generando pruebas funcionales en aplicaciones Web en diversos lenguajes como java, python, javascript, etc.

Selenium está dividida en 4 proyectos:
* [Selenium IDE](http://docs.seleniumhq.org/projects/ide/): Es un plugin para la aplicación Firefox, con el cual podemos capturar y ejecutar un conjunto de acciones (o pruebas) dentro del navegador, con opción de generar scripts para el almacenamiento en disco y/o modificación manual.
  * los scripts son un conjunto de instrucciones o pasos que pueden ser exportadas en distintos formatos como HTML, Java, etc.
  * Cada paso tiene 3 propiedades:
    * Commando a ejecutar
    * Objetivo (opcional dependiendo del comando) donde se ejecutara el comando, este puede ser localizado por el ID, nombre, CSS, DOM o XPATH, este último es mas recomendable cuando las pruebas son muy dinamicas, ya que es un lenguaje robusto para localizar elementos dentro de una estructura XML, es recomendable leer
    * Valor (opcional dependiendo del comando) esperado despues de ejecutar el comando
  * La desventaja de usar unicamente Selenium IDE es que se está limitado a sólo poder ejecutarse en Firefox.
  * Existe una alternativa llamada [SeleniumBuilder](http://sebuilder.github.io/se-builder/) la cual ofrece algunas funcionalidades extras o mas avanzadas.
* [Selenium Remote Control (Selenium RC)](http://docs.seleniumhq.org/projects/remote-control/): Es un servidor RESTful que ejecuta instrucciones vía http y las ejecuta en el navegador que se le indique.
  * Se puedenutilizar los scripts generados por Selenium IDE, los cuales deben de ser interpretados por una [librería cliente](https://github.com/search?q=selenium+rc&type=Repositories&ref=searchresults) que le envía las instrucciones a SeleniumRC
* [Selenium WebDriver](http://docs.seleniumhq.org/projects/webdriver/): Es una interface para el control del navegador, la cual ya está implementado para los navegadores más comunes.
* [Selenium Grid](http://docs.seleniumhq.org/projects/webdriver/): Permite ejecutar en paralelo varios Selenium RC para realizar pruebas de concurrencia.

El El proceso recomendado para optimizar esfuerzos al usar Selenium es generar los Scripts con SeleniumIDE o SeleniumBuilder y ejecutarlos en Selenium RC.
