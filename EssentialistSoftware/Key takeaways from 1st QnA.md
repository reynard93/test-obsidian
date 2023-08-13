-  _The reason why testing is so hard to learn is because it is linked directly to **design, architecture & strategy.**_
- The fastest way to become a better architect is to understand the stereotypically first principled starting point for ALL architectures.
	- _You want to learn to **separate concerns** into the correct layers, understand the **roles** that exist at those layers, and then understand the **stereotypical collaborations** between the roles at those layers._
	- ![[Pasted image 20230813143838.png]]
- _**Vertical Slicing (at the Customer & Developer Boundaries)** — Once you understand that there’s a stereotypical architecture, one might wonder: “How do you implement features within this? What does that look like on the backend? What does it look like on the frontend? How do you even **kick off** a feature?”. We slice vertically from one of two boundaries. The Customer and the Developer boundaries._
- ![[Pasted image 20230813143918.png]]
_**The Ideal Developer Workflow: How to Make Architecture, Design & Testing Easy & Consistent on Any Layer of The Stack —** Putting all of this together, we learn how to go from zero (on a new project) to having your development environment set up with a testable architecture (on any stack) so that you can spend 80% of your time developing out features using tests — tests that actually test your features, not your frameworks, libraries, or infrastructure. The remaining 20%? Setting up your features._
![[Pasted image 20230813143948.png]]
![[Pasted image 20230813144010.png]]

_**Systems Thinking & System Verification (at various Guess Points)** — Another reason testing is so hard is because you have to verify the System you’re currently testing, in a variety of different ways (I call this System Verification). There are three: **result, state & communication.**_

 _**Systems Thinking**
 - each **Guess Point** is just one **Input-Output System** in a chain of Input-Output Systems, which at the entry point is the **Problem System** and at the very end is the **Execution System** (where the User is using the software).
![[Pasted image 20230813144621.png]]
_**How to use FA²STR to Nth Loop Inwards (Outside-In TDD) —** When you move inwards, from one Guess Point to the next, you have to use FA²STR to kick off your work. This process, of moving in a layer, is called Nth-Looping (or Outside-In TDD). We learn_

_**Why You Should First Deploy a Walking Skeleton —** We talked about why you want to always Build, Walk & Deploy a Skeleton of the architecture you need, right away before diving into anything else._

_**The Stereotypical FRONTEND Architecture —** We talked about the way that the stereotypical architecture applies to a Frontend Application._
![[Pasted image 20230813144737.png]]

here are all the diagrams:
https://www.figma.com/file/yHsqafId4XvjTAAladxLDc/Q%26A%3A-May-5th---Front-loading-The-Value?type=whiteboard&node-id=0%3A1&t=8Do2isI696AKyw2j-1