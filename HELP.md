# Ontimize Classic Project
## Prerequisites
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
<table>
  <tr>
    <td>Maven</td>
    <td>Application</td>
  </tr>
  <tr>
    <td>

```  
cd *-server  
mvn exec:java -Prun_server
```  

</td>
    <td>

    JDK ---------------→ 1.8
    Classpath module --→ *-server
    Server main method → com.imatia.classic.server.ProjectServerLauncher
    Server argument --→ com/imatia/classic/server/conf/server.properties
   </td>
  </tr>
</table>

## Launch client
<table>
  <tr>
    <td>Maven</td>
    <td>Application</td>
  </tr>
  <tr>
    <td>

```  
cd *-client  
mvn exec:java -Prun_client  
```  

</td>
    <td>

    JDK ---------------→ 1.8
    Classpath module --→ *-client
    Client main method → com.imatia.classic.client.ClientLauncher
    Client argument 1 -→ com/imatia/classic/client/conf/labels.xml
    Client argument 2 -→ com/imatia/classic/client/clientapplication.xml
    Client argument 3 -→ -conf
    Client argument 4 -→ com/imatia/classic/client/conf/defaultXmlConfigurationParameters.xml
   </td>
  </tr>
</table>

To enable Look&Feel, add the next lines to VM params
```  
-Dcom.ontimize.gui.lafclassname="com.ontimize.plaf.OntimizeLookAndFeel"  
-Dcom.ontimize.gui.lafstyle="com/ontimize/plaf/style/whiteStyle.css"  
```