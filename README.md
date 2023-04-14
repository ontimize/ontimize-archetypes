# Aplicación base arquetipo Ontimize Boot
Esta aplicación es una **aplicación base** que se usa para generar el arquetipo de una aplicación que usa Ontimize Boot. Esto significa que cualquier cambio que se desee hacer al arquetipo, se debe hacer en esta aplicación, que generará el nuevo arquetipo a partir de su estructura e información.

El arquetipo se genera a través de *GitHub Actions*. Estas actions están guardadas en la carpeta <code>.github</code> por
lo que **esta carpeta no debe de modificarse**.

## Cambios que se realizan sobre el proyecto en el arquetipo
* **MANUAL**: El arquetipo **NO PUEDE** contener el fichero ***templateDB.script*** de la base de datos. Si se hace un cambio en la base de datos, después de cerrar correctamente la base de datos con el comando sql <code>SHUTDOWN</code>, el fichero *templateDB.script* contendrá el estado de la base de datos con el estado en el que se quedó, por lo que borraremos el fichero *templateDB.txt* y **renombraremos la extensión del fichero *templateDB.script* a \*.txt**.
* *AUTOMÁTICO*: Se elimina cualquier rastro de las *GitHub Actions* para el despliegue del arquetipo en *Maven Central* .
* *AUTOMÁTICO*: Este fichero *README.md* se elimina, y **se renombra el fichero HELP.md como el README.md del arquetipo**.
* *AUTOMÁTICO*: Se cambia el *groupId* del proyecto, pasando de ser *com.imatia* a *com.ontimize*. El empleo de *com.imatia* es necesario para evitar una sustitución incorrecta entre los paquetes y los imports.

## ¿Cómo usar el arquetipo?
El arquetipo lo podemos usar ejecutando el siguiente comando de Maven en la carpeta que queramos ubicar el proyecto.
```
mvn -B archetype:generate -DgroupId=YOUR_PROJECT_GROUP_ID -DartifactId=YOUR_PROJECT_ARTIFACT_ID -Dversion=YOUR_PROJECT_VERSION -Dpackage=YOUR_PROJECT_PACKAGE -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot-backend-archetype -DarchetypeVersion=99.9.9-SNAPSHOT -DinteractiveMode=false
```
## ¿Porqué se usa la versión 99.9.9-SNAPSHOT?
Empleamos esta versión a modo de versión ***latest***, de tal manera que se pueda usar siempre esta versión para que contenga el último arquetipo generado. Al ser una versión *SNAPSHOT*, nos permite actualizar la versión sin generar un marcador nuevo.

## ¿Puedo desplegar una version final en vez de la 99.9.9-SNAPSHOT?
Por supuesto, cuando se ejecuta la action, hay que indicar el el input la versión que se quiere desplegar. Hay que conocer la última versión desplegada para escribir la siguiente versión correspondiente. Generará la version 99.9.9-SNASHOT, le cambiará la versión por la indicada deplegará en *Maven Central* una versión con esa numeración. **NO HAY** que modificar en ningún momento la versión del proyecto.

## ¿Cómo probar el arquetipo?
#### Descargando el fichero que se genera en GitHub Action
Descarga y descomprime (extensión *\*.tar.gz*) el fichero **backend-zip** que se encuentra añadido al resumen de la ejecución de la action del despliegue del arquetipo para tener una carpeta con el proyecto creado.
![image](https://i.imgur.com/rdyvGmI.png)
#### Ejecutando el comando Maven
Ejecutar el siguiente comando Maven, que es el mismo que ejecuta la GitHub Action del paso anterior.
```
mvn -B archetype:generate -DgroupId=com.example -DartifactId=backendtest -Dversion=1.0.0-SNAPSHOT -Dpackage=com.ontimize.backendtest -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot-backend-archetype -DarchetypeVersion=99.9.9-SNAPSHOT -DinteractiveMode=false
```
