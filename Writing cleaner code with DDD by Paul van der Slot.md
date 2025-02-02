## Writing cleaner code with DDD by Paul van der Slot
https://www.youtube.com/watch?v=3t0tZTOGk08

### Ubiquitous language
A value object:: an immutable type that is distinguishable only by the state of its properties
<!--SR:!2022-10-25,1,230-->
center of gravity for complex biz logic, immutable easy to test
vs utility method, need to know it exists, you dont know if email is validated alrdy later
, vo: everywhere email is validated, type safe, explicit domain meaning
- avoid primitive obsessions -> move to domain primitives

tell don't ask
tell an obj what to do instead of asking internal data to do it yourself, add bvr in the obj the data belongs to

getters and setters are evil
- combination of setters have meaning, can forget to set 1/>

### Supple Design
	loosely coupled
	highly cohesive
	able to change

Tie togeher vs Stick together (coupling vs cohesion)
coupling has to do with change, if a change b has to change

cohesion - one thing change everything has to change, attempting to divide a cohesive class would only result in increased coupliing and decreased readability
	has a lot to do with: SRP and SoC

benefits - increased testability (single purpose / less dependencies), maintainability ( impact of changes dcr bcz they are in one place ), reusability increases (units have a single purpose)

intention revealing interfaces
	if a method name isn't clear, have to look within to see what it is for, or inside the next mtd (repeat)

side effect free functions
	they cannot be prevented: update db, web svc calls, send msg but they happen at edge of app, in doman logic, can use pure functions a lot
	imperative shell will contain code with side effects
	![[Pasted image 20221024085933.png]]

### Bounded Context
different groups have different views on the same model
it is the boundary within a domain where a particular domain model applies
ubiq language unique per bounded context, a natural way to split up your model

DRY vs Coupling across bounded contexts, Can't have both
if we want to have DRY we will increase coupling, there is a trade-off
inside a BC, DRY is very important
reducing coupling is more important across bounded contexts
	why?
	autonomous, can evolve alone
	decreased cognitive load -> only have to think about own bounded context
	![[Pasted image 20221024092355.png]]
	event storming can help with discovery