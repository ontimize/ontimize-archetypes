[![Ontimize Classic Archetype](https://img.shields.io/maven-central/v/com.ontimize/ontimize-classic-archetype?label=Latest%20Ontimize%20Boot%20archetype&style=flat-square)](https://maven-badges.herokuapp.com/maven-central/com.ontimize/ontimize-classic-archetype)

# Ontimize Classic archetype base application
This application is a **base application** used to generate the archetype of an application that uses Ontimize Classic. This means that any changes you want to make to the archetype must be made in this application, which will generate the new archetype from its structure and information.

The archetype is generated through *GitHub Actions*. These actions are stored in the <code>.github</code> folder so **this folder should not be modified**.

## Changes made to the project in the archetype
* **MANUAL**: The archetype **CANNOT** contain the file ***templateDB.script*** of the database. If a change is made to the database, after correctly closing the database with the sql command <code>SHUTDOWN</code>, the *templateDB.script* file will contain the state of the database with the state it was left in, so we will delete the *templateDB.txt* file and **rename the extension of the *templateDB.script* file to \\*.txt**.
* **MANUAL**: The archetype **CANNOT** contain the file ***license.dat***.
* *AUTOMATIC*: Any trace of the *GitHub Actions* for deploying the archetype in *Maven Central* are removed.
* *AUTOMATIC*: This *README.md* file is deleted, and **the HELP.md file is renamed as the archetype's README.md**.
* *AUTOMATIC*: The project's *groupId* is changed, going from *com.imatia* to *com.ontimize*. The use of *com.imatia* is necessary to avoid incorrect substitution between packages and imports.
* *AUTOMATIC*: The *pom.xml* file on the server modifies the package of the class running in the launch profile, as well as its properties file, and both contain the correct path based on the *package* set at generation.
* *AUTOMATIC*: The *locator.properties* and *server.properties* file paths will be modified to the corresponding path in the *package* setted in the project generation.
* *AUTOMATIC*: The *pom.xml* file on the client modifies the package of the class running in the launch profile, as well as its properties files, and contains the correct path based on the *package* set at generation.
* *AUTOMATIC*: The *clientapplication.xml* file paths will be modified to the corresponding path in the *package* setted in the project generation.

## How to use the archetype?
The archetype can be used by executing the following Maven command in the folder where we want to place the project.
```
mvn -B archetype:generate -DgroupId=com.example -DartifactId=demo -Dversion=1.0.0-SNAPSHOT -Dpackage=com.example.demo -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-classic-archetype -DarchetypeVersion=99.9.9-SNAPSHOT -DinteractiveMode=false
```

## Why is version 99.9.9-SNAPSHOT used?
We use this version as a ***latest*** version, so that this version can always be used to contain the last generated archetype. Being a *SNAPSHOT* version, it allows us to update the version without generating a new marker.

## Can I deploy a final version instead of 99.9.9-SNAPSHOT?
Of course, when executing the action, the version to be deployed must be indicated in the input. You must know the last version deployed to write the next corresponding version. It will generate the version 99.9.9-SNASHOT, it will change the version for the indicated one and it will deploy in *Maven Central* a version with that numbering. There is **NO NEED** to change the version of the project at any time.

## How to test the archetype?
#### Downloading the file that is generated in GitHub Action
Download and unzip (extension *\*.tar.gz*) the **backend-zip** file that is added to the summary of the archetype deployment action execution to have a folder with the project created.
![image](https://i.imgur.com/sfGVdh2.png)
#### Running the Maven command
Execute the following Maven command, which is the same command that executes the GitHub Action from the previous step.
```
mvn -B archetype:generate -DgroupId=com.example -DartifactId=demo -Dversion=1.0.0-SNAPSHOT -Dpackage=com.example.demo -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-classic-archetype -DarchetypeVersion=99.9.9-SNAPSHOT -DinteractiveMode=false
```
