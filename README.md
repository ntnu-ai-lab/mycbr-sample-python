# Explanation how to run the API before you can run the script(s)

Example iPython notebooks that showcase the myCBR Rest API's functionalities.

## Pre-requisites
Before you can run the scripts you have to deploy your project using the Rest API. This requires two components: the myCBR SDK as well as the myCBR Rest API.

## Getting the myCBR SDK
You can clone the source code here: https://github.com/ntnu-ai-lab/mycbr-sdk and build and deploy it using the following command using maven:
```
cd mycbr-sdk 
mvn clean install 
```
Please note that maven must be installed to build myCBR. 
With these commands you first go into the myCBR folder and then build the SDK.

## Getting the myCBR Rest API
You can clone the source code here: https://github.com/ntnu-ai-lab/mycbr-rest and build and deploy it using the following command using maven:
```
cd mycbr-rest 
mvn clean install
or
mvn clean install -DskipTests=True
```
Please note that maven must be installed to build myCBR Rest. 
With these commands you first go into the myCBR folder and then build the Rest.

## Getting the myCBR Rest API

Next you will have to download and build the Rest API. As the Rest API uses the myCBR SDK you need to install is using the following command: 
```
cd ../mycbr-rest 
mvn install:install-file -Dfile=../mycbr-sdk/target/myCBR-x.x-SNAPSHOT.jar -DpomFile=../mycbr-sdk/pom.xml -DlocalRepositoryPath=lib/no/ntnu/mycbr/mycbr-sdk/
```
For these calls we assume that both the mycbr-sdk and mycbr-rest are located in the same folder:
```
root
 |__ mycbr-sdk
          |__pom.xml
          |__src
          |__target
               |__myCBR-x.x-SNAPSHOT.jar
 |__ mycbr-rest
          |__pom.xml
          |__src
          |__target
               |__mycbr-rest-x.x-SNAPSHOT.jar
          |__lib/no/ntnu/mycbr/mycbr-sdk/
```
Once myCBR is installed you can build the Rest API:
```
cd mycbr-rest 
mvn clean install 
```
The last step is starting the server with a specific project:
```
java -DMYCBR.PROJECT.FILE=/absolute/path/to/project.prj -jar ./target/mycbr-rest-x.x-SNAPSHOT.jar 
```
When using the commands, pleaes ensure that the correct software version are used instead of "x".

## Running example 
Assuming you're either in the mycbr-rest or mycbr-sdk folder, this call is for building the sdk, deploying it, building the Rest API and running it:

```
cd ../mycbr-sdk ; mvn clean install ; cd ../mycbr-rest ; mvn install:install-file -Dfile=../mycbr-sdk/target/myCBR-3.3-SNAPSHOT.jar -DpomFile=../mycbr-sdk/pom.xml -DlocalRepositoryPath=lib/no/ntnu/mycbr/mycbr-sdk/ ; mvn clean install ; java -DMYCBR.PROJECT.FILE=/tmp/used_cars_flat.prj -jar ./target/mycbr-rest-1.0-SNAPSHOT.jar
```
