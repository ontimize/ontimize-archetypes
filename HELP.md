# Ontimize Classic Project
## Prerequisite
* Java 1.8
## First init
```
mvn install
```
## Launch database
```
cd *-server
mvn exec:java -Prun_database
```
## Launch server
```
cd *-server
mvn exec:java -Prun_server
```
## Launch client
```
cd *-client
mvn exec:java -Prun_client
```
To enable Look&Feel, add the next lines to VM params
```
-Dcom.ontimize.gui.lafclassname="com.ontimize.plaf.OntimizeLookAndFeel" 
-Dcom.ontimize.gui.lafstyle="com/ontimize/plaf/style/whiteStyle.css"
```