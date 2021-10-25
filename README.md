
# Ontimize Boot

- Enter the parent directory and run an install:
	
		mvn install
	
## Start only the server: 
 - Go to the `boot` folder and run the command

		mvn spring-boot:run

## Run the client alone, outside the spring-boot server

 - Go to the `frontend/src/main/ngx` folder, if you have node and npm installed on your system run the following commands:

		npm install
		npm start 

## Deploy and run client and server together
 - If you want to deploy the client and server together, run the following command 

		mvn clean install -Pdeploy

 - Go to the `boot/target` folder and run the command
 
 		java -jar <name_of_the_boot_jar>
	
Use the following URL to access the [http://localhost:33333/app/index.html](http://localhost:33333/app/index.html) application 
