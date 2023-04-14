# Aplicación base arquetipo Ontimize Boot
Esta aplicación es una **aplicación base** que se usa para generar el arquetipo de una aplicación que usa Ontimize Boot. Esto significa que cualquier cambio que se desee hacer al arquetipo, se debe hacer en esta aplicación, que generará el nuevo arquetipo a partir de su estructura e información.

El arquetipo se genera a través de *GitHub Actions*. Estas actions están guardadas en la carpeta <code>.github</code> por
lo que **esta carpeta no debe de modificarse**.

## Cambios que se realizan sobre el proyecto en el arquetipo
* **MANUAL**: El arquetipo **NO PUEDE** contener el fichero ***templateDB.script*** de la base de datos. Si se hace un cambio en la base de datos, después de cerrar correctamente la base de datos con el comando sql <code>SHUTDOWN</code>, el fichero *templateDB.script* contendrá el estado de la base de datos con el estado en el que se quedó, por lo que borraremos el fichero *templateDB.txt* y **renombraremos la extensión del fichero *templateDB.script* a \*.txt**
* *AUTOMÁTICO*: Se elimina cualquier rastro de las *GitHub Actions* para el despliegue del arquetipo en *Maven Central* 
* *AUTOMÁTICO*: Este fichero *README.md* se elimina, y **se renombra el fichero HELP.md como el README.md del arquetipo**

## ¿Cómo usar el arquetipo?
El arquetipo lo podemos usar ejecutando el siguiente comando de Maven en la carpeta que queramos ubicar el proyecto
```
mvn -B archetype:generate -DgroupId=YOUR_PROJECT_GROUP_ID -DartifactId=YOUR_PROJECT_ARTIFACT_ID -Dversion=YOUR_PROJECT_VERSION -Dpackage=YOUR_PROJECT_PACKAGE -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot-backend-archetype -DarchetypeVersion=1.0.5-SNAPSHOT -DinteractiveMode=false
```
## ¿Cómo probar el arquetipo?
#### Descargando el fichero que se genera en GitHub Action
Descarga y descomprime (extensión *\*.tar.gz*) el fichero **backend-zip** que se encuentra añadido al resumen de la ejecución de la action del despliegue del arquetipo para tener una carpeta con el proyecto creado
![image](https://i.imgur.com/DOpyK5M.png)
#### Ejecutando el comando Maven
Ejecutar el siguiente comando Maven, que es el mismo que ejecuta la GitHub Action del paso anterior
```
mvn -B archetype:generate -DgroupId=com.example -DartifactId=backendtest -Dversion=1.0.0-SNAPSHOT -Dpackage=com.ontimize.backendtest -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot-backend-archetype -DarchetypeVersion=1.0.5-SNAPSHOT -DinteractiveMode=false
```
