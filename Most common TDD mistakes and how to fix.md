# Most common TDD mistakes and how to fix
https://www.youtube.com/watch?v=-4Ybn0Cz2oU&ab_channel=GOTOConferences

tdd - gives us feedback on our design quality, if our tests are difficult to write, our design is poor

### the liar
	passes all but uselss assertions
cause: chase test coverage, bcz not doing tdd

### excessive setup
	requires lots of work to be ready to test
cause: not tdd (i.e write code first b4 test), poor modularity and soc
fix: improve abstraction and separation of concerns
*minute 9:20+ shows an example, with jenkins localhost test*

### the giant
	many lines of code & assertions
cause: no tdd, often created as 'component tests'
problem: difficult to understand, high coupling (btwn test and code), hard to maintain
fix: decompose into multiple test cases, one assertion per test

### the mockery
	uses so many mocks that real code isn't tested
cause: excessive setup, high coupling (btwn test and code)
problem: does nothing
fix: abstract and soc, review design of code (think of testing as a tool to achieve some outcome)
*focus on bvr your wan from yr software rather than the technical implementation*

### the inspector
	violates encapsulation in order to make assertions
cause: no tdd, chase test coverage, poor DI
problem: small changes in code breaks tests
fix: never compromise encapsulation for testing, same fix (soc) etc, design for testability
use mocks or stubs to provide measurement points, get info about what is happening
