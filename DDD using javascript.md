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
this service is just a different file put it at a separate place so you can test it separately

gf on the line gets the definitons etc (f for full?)
gd goes to definition
gi goes to implementation (go into file immediately)
go to error suggested by lsp by ]D, [D to go backwards

leader ca to see code actions

leader d to see the error on the line

shift + k to get more documentation on where your cursor is