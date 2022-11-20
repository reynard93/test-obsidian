maybe can use ddd using typescript too
![[Pasted image 20221120151035.png]]
we call respository apis/services

the form (the public contract of my repository) is independent from the data src (data src can come from many places)

the purpose of a repository is to produce and store entities
a json is almost always an entity, id 

example: business rules on what is required for promotion
	1: avg votes should be > 7
	2: require min 4 votes

https://youtu.be/8AUxhphOl5I
27:09 starting ddd refactoring

a service::an object that orchestrates the steps required to fulfill the cmds imposed by the client
	3 kinds of services
	- Domain
	- Application
	- Infras
these classifications lose importance for a fe app