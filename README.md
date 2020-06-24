# Microservice Demo Solution

This sample aims to demonstrate a simple yet complete microservice solution. See the [documentation](https://abp.io/documents/abp/latest/Samples/Microservice-Demo).

## Build
[## Open & Build the Visual Studio Solution](https://docs.abp.io/en/abp/latest/Samples/Microservice-Demo#open-build-the-visual-studio-solution)
Open the samples\MicroserviceDemo\MicroserviceDemo.sln in Visual Studio 2017 (15.9.0+).
Run dotnet restore from the command line inside the samples\MicroserviceDemo folder.
Run dotnet build from the command line inside the samples\MicroserviceDemo folder.
Build the solution in Visual Studio.


[## MsDemo_Identity Database](https://docs.abp.io/en/abp/latest/Samples/Microservice-Demo#msdemo_identity-database)

Right click to the AuthServer.Host project and click to the Set as startup project.
Open the Package Manager Console (Tools -> Nuget Package Manager -> Package Manager Console)
Select AuthServer.Host as the Default project.
Run Update-Database command.

[## MsDemo_ProductManagement](https://docs.abp.io/en/abp/latest/Samples/Microservice-Demo#msdemo_productmanagement)

Right click to the ProductService.Host project and click to the Set as startup project.
Open the Package Manager Console (Tools -> Nuget Package Manager -> Package Manager Console)
Select ProductService.Host as the Default project.
Run Update-Database command.

[## Run Projects](https://docs.abp.io/en/abp/latest/Samples/Microservice-Demo#run-projects)
Run the projects with the following order (right click to each project, set as startup project an press Ctrl+F5 to run without debug):

- [] AuthServer.Host
- [] IdentityService.Host
- [] TenantManagementService.Host
- [] BloggingService.Host
- [] ProductService.Host
- [] InternalGateway.Host
- [] BackendAdminAppGateway.Host
- [] PublicWebSiteGateway.Host
- [] BackendAdminApp.Host
- [] PublicWebSite.Host

-----------------------------------------------------------------------------------------
# Conatiner Steps

## Rabbitmq
- docker run -it --rm --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management
http://localhost:15672/#/

-------------------------------------
## Redis :

- docker run -d -p 6379:6379 --name redis1 redis         

- docker exec -it redis1 sh
- [#] redis-cli
- 127.0.0.1:6379> ping
- PONG
--------------------------------------
## Elasticsearch :

- docker  network create somenetwork
- docker run -d --name elasticsearch --net somenetwork -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" elasticsearch:7.7.1
                      
http://localhost:9200/

## Kibana : 

- docker run -d --name kibana --net somenetwork -p 5601:5601 kibana:7.7.1

http://localhost:5601/app/kibana#/home

---------------------------------------
## Mongodb :

- docker run -d -p 27017-27019:27017-27019 --name mongodb mongo:4.0.4

- docker exec -it mongodb bash

- mongo

---------------------------------------
# Stop & Remove Containers
---------------------------------------
## stop all containers:
docker kill $(docker ps -q)

## remove all containers
docker rm $(docker ps -a -q)

## remove all docker images
docker rmi $(docker images -q)
