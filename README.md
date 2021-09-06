# Ontimize archetypes

This repository contains the different projects from which the archetypes for the different Ontimize archetypes are created

Each branch of this repository contains a project that serves to create the associated archetype. The different archetypes available are listed below

-   [Ontimize Boot with Ontimize Web 8.X.X frontend](https://github.com/ontimize/ontimize-archetypes-projects/tree/ontimize-boot-web-8)
-   [Ontimize Boot](https://github.com/ontimize/ontimize-archetypes-projects/tree/ontimize-boot-backend)
-   [Ontimize Boot with Ontimize Web 8.X.X (without Maven) frontend](https://github.com/ontimize/ontimize-archetypes-projects/tree/ontimize-boot-web-8-nomaven)


**If you want to create an archetype from a local project, look at the following steps:**

## Generate the base-archetype

Go to the parent project and run the following command:

> $ mvn archetype:create-from-project

This will generate a bulk of files under the `target/generated-sources/archetype` directory.

From this folder structure you can discard the `target` directory sub-tree, just `mvn clean` it.

## Adjusting the archetype

You can modify the archetype any way you want (more info [here](https://geekofficedog.blogspot.com/2013/08/creating-maven-archetypes-tutorial.html)), but the most important file you need to check is `archetype-metadata.xml` located under the `src/main/resources/META-INF/maven` directory. This file groups the resources as file sets that are going to be filtered by the archetype during the generation process.

You need to modify the property `start-class` on the pom.xml of the `boot` module located under `target/generated-sources/archetype/src/main/resources/archetype-resources`. Just replace the package of ServerApplication for `${package}.ServerApplication`


## Creating the archetype

You only have to go to the `target/generated-sources/archetype` and run:

> $ mvn install

This will re-generate the `target` folder and the `archetype-generated.jar` file of the archetype.

## Test your archetype locally

The `mvn install` line executed in the previous section will generate a file `archetype-catalog.xml` in your `~/.m2` directory with the archeype data like `groupId`, `artifactId` and `version`.

To generate a new project from this archetype run the command:

> $ mvn archetype:generate

Your newly deployed archetype will be listed as the last one of a list that will appear in your terminal, choose the archetype, fill in the parameters and hit enter, open up your file browser and check that all the generated files accomodates to the supplied parameters.
