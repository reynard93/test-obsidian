strategic design - what, why, big pic, event storming

![[Pasted image 20221024172951.png]]
CQRS principle
	command: does something does NOT return
	query returns a result but does NOT change state
	boundaries btwn 1) manipulate data 2) does not manipulate data
how to follow it ->
commandservice, queryservice