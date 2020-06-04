# Ontimize Boot
This branch contains the project that generates the Ontimize Boot archetype with the Ontimize Web 4 frontend.

The command to create an application using this archetype is the following:

    mvn org.apache.maven.plugins:maven-archetype-plugin:2.4:generate 
    -DgroupId=YOUR_GROUP_ID
    -DartifactId=YOUR_ARTIFACT_ID
    -Dversion=YOUR_VERSION
    -DarchetypeGroupId=com.ontimize 
    -DarchetypeArtifactId=ontimize-boot 
    -DarchetypeVersion=1.0.0 
    -DinteractiveMode=false 
    -DarchetypeCatalog=https://artifactory.imatia.com/public-artifactory/ontimize-archetypes/archetype-catalog.xml
