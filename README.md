[![Ontimize Boot Archetype](https://img.shields.io/maven-central/v/com.ontimize/ontimize-boot-backend-archetype?label=Latest%20Ontimize%20Boot%20archetype&style=flat-square)](https://maven-badges.herokuapp.com/maven-central/com.ontimize/ontimize-boot-backend-archetype)

# Ontimize Boot archetype base application
This application is a **base application** used to generate the archetype of an application that uses Ontimize Boot. This means that any changes you want to make to the archetype must be made in this application, which will generate the new archetype from its structure and information.

The archetype is generated through *GitHub Actions*. These actions are stored in the <code>.github</code> folder so **this folder should not be modified**. 

## Changes made to the project in the archetype
* **MANUAL**: The archetype **CANNOT** contain the file ***templateDB.script*** of the database. If a change is made to the database, after correctly closing the database with the sql command <code>SHUTDOWN</code>, the *templateDB.script* file will contain the state of the database with the state it was left in, so we will delete the *templateDB.txt* file and **rename the extension of the *templateDB.script* file to \\*.txt**.
* *AUTOMATIC*: Any trace of the *GitHub Actions* for deploying the archetype in *Maven Central* are removed.
* *AUTOMATIC*: This *README.md* file is deleted, and **the HELP.md file is renamed as the archetype's README.md**.
* *AUTOMATIC*: The project's *groupId* is changed, going from *com.imatia* to *com.ontimize*. The use of *com.imatia* is necessary to avoid incorrect substitution between packages and imports.

## How to use the archetype?
The archetype can be used by executing the following Maven command in the folder where we want to place the project.
```
mvn -B archetype:generate -DgroupId=YOUR_PROJECT_GROUP_ID -DartifactId=YOUR_PROJECT_ARTIFACT_ID -Dversion=YOUR_PROJECT_VERSION -Dpackage=YOUR_PROJECT_PACKAGE -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot-backend-archetype -DarchetypeVersion=99.9.9-SNAPSHOT -DinteractiveMode=false
```
## Why is version 99.9.9-SNAPSHOT used?
We use this version as a ***latest*** version, so that this version can always be used to contain the last generated archetype. Being a *SNAPSHOT* version, it allows us to update the version without generating a new marker.

## Can I deploy a final version instead of 99.9.9-SNAPSHOT?
Of course, when executing the action, the version to be deployed must be indicated in the input. You must know the last version deployed to write the next corresponding version. It will generate the version 99.9.9-SNASHOT, it will change the version for the indicated one and it will deploy in *Maven Central* a version with that numbering. There is **NO NEED** to change the version of the project at any time.

## When I try to use the archetype, it responds that the version is not found.
This error occurs becase the command is trying to get the *latest* version (*99.9.9-SNAPSHOT*). This problem occurs because by default, ***SNAPSHOT versions cannot be accessed from Maven Central***. For it, it is necessary to activate, in the *settings.xml* file, the access to the SNAPSHOT versions of Maven Central. In case we do not have this file, we have to create it ***inside*** the .m2 folder (*by default, it is in the following path: ~/.m2*). [Here is an example](https://gist.github.com/supportcampusdual/fa55eb0fa7fd91f825abcc557a1f730d) of the *settings.xml* file content to enable SNAPSHOT versions:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0" 
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
  <profiles>
	<profile>
		<id>ossrh</id>
		<repositories>
			<repository>
				<id>ossrh-snapshot</id>
				<url>https://s01.oss.sonatype.org/content/repositories/snapshots/</url>
				<snapshots>
					<enabled>true</enabled>
				</snapshots>
			</repository>
		</repositories>
	</profile>
  </profiles>
  <activeProfiles>
	<activeProfile>ossrh</activeProfile>
  </activeProfiles>
</settings>
```
In case you do not allow the use of SNAPSHOT versions, the latest available release version can be used. In this case, replace the SNAPSHOT version of the archetype (-DarchetypeVersion=99.9.9-SNAPSHOT), with the latest release version, which is the following (without the v): [![Ontimize Boot Archetype](https://img.shields.io/maven-central/v/com.ontimize/ontimize-boot-backend-archetype?label=&style=flat-square)](https://maven-badges.herokuapp.com/maven-central/com.ontimize/ontimize-boot-backend-archetype)

> **_NOTE:_**  The release version may not have the latest changes made to the archetype.
## How to test the archetype?
#### Downloading the file that is generated in GitHub Action
Download and unzip (extension *\*.tar.gz*) the **backend-zip** file that is added to the summary of the archetype deployment action execution to have a folder with the project created.
![image](https://i.imgur.com/rdyvGmI.png)
#### Running the Maven command
Execute the following Maven command, which is the same command that executes the GitHub Action from the previous step.
```
mvn -B archetype:generate -DgroupId=com.example -DartifactId=backendtest -Dversion=1.0.0-SNAPSHOT -Dpackage=com.ontimize.backendtest -DarchetypeGroupId=com.ontimize -DarchetypeArtifactId=ontimize-boot-backend-archetype -DarchetypeVersion=99.9.9-SNAPSHOT -DinteractiveMode=false
```
