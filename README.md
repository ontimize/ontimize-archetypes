
# Ontimize Boot
This branch contains the project that generates the Ontimize Web 8 frontend.

- The command to create an application using this archetype is the following:

	    mvn org.apache.maven.plugins:maven-archetype-plugin:2.4:generate -DgroupId=YOUR_GROUP_ID -DartifactId=YOUR_ARTIFACT_ID -Dversion=YOUR_VERSION -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot -DarchetypeVersion=1.0.0 -DinteractiveMode=false -DarchetypeCatalog=https://artifactory.imatia.com/public-artifactory/ontimize-archetypes/archetype-catalog.xml

## Run the client

- Go to the `frontend/src/main/ngx` folder, if you have node and npm installed on your system run the following commands:

		npm install
		npm start 
	
Use the following URL to access the [http://localhost:4299/](http://localhost:4299/) application 
