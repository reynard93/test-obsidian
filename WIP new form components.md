
ignore repeatedKey and repeatedNumber think about way to achieve same concept without this
	repeatedKey and repeatedNumber must always be stored togehter
how about dnt implement repeatedkey and repeatednumber first **formListNode** component
i know why the . or / stuff is required now

poc keep it basic remove this
		// seems to be set for fieldID repeated key look at old form components computed state()
		function _setInputStateObject(fieldId) {
			// ... Your function implementation
		}

i dont need .init if i not doing the repeated stuff shenanigans

so somehow beforeDestroy is used in the component to be able to destroy itself, is there really such a need? i guess there is, because when parts of the form change the input should disappear etc, but not from v-if toggled to false the component gets destroyed, i dont see the usecase as of now
	TRY to use the mutation observer to track node changes and remove the node from there

repeatedNumber and repeatedKey is only applicable for QualificationItem on sat form atm

		function _validateChildren(nodes, acc) {
			// ... Your function implementation
		}

		async function _validateDescendantFormFacilitator() {
			// ... Your function implementation
		}

only applies to repeated,
repeated reuses the same schema and the form store is an array according to current implementation
 all this stuff should be covered under a wrapper stepper component and not part of the formfacilitator imo, this wrapper should orchestrate the different form facilitators

we can simplify it, if errorMessage is there means input state invalid, inputState be only for form facilitator which determiens whether this partiuclar accordion is completed or  not

if i dont want the repeated things what i pass in as the state is the state

dependency seems only used for selection etc so far, backlog it

This is under formfaciliitator onMounted hook, also removed at the end of onMounted the second line. TODO: make use of emit by children onDestroy pass that to form Facillitator to listen
``
```
// better way is for children to emit when they are gone, more performant 
// feel like everything around this is complicated around the 'repeated' stuff, these code here seems to be to facilitate that as well
instead of having the mutation observer runnning
let observer: MutationObserver | null = null
 ref="facilitatorEl" // required if using this mutation approach

	observer = new MutationObserver(mutations => {
		// replaces the need to have onDestroy hook getting _onDestroy method
		for (const mutation of mutations) {
			if (mutation.type === 'childList') {
				console.log('Child node added or removed:', mutation.addedNodes, mutation.removedNodes);
				// get removed node's field id
				if (mutation.removedNodes.length) {
					for (const removedNode of mutation.removedNodes) {
						if (removedNode instanceof Element && removedNode.hasAttribute('field-id') {
							const fieldId = removedNode.getAttribute('field-id')
							if (fieldId) {
								// remove from childNodes
								// also note i want to find the most parent node with fieldId, would be nice to skip nodes below for removedNodes
								delete childNodes[fieldId]// not sure if removedNode has fieldID should test
							}
						}
					}
				}
			}
		}

		_renderChildComponents(props.$children)
	})

	observer.observe(facilitatorEl.value as unknown as Node, { attributes: false, childList: true, characterData: false, subtree: true })


// this line is outside of unmounted
onBeforeUnmount(() => {
	if(observer) {
		observer.disconnect()
	}
})
```

validation happens within formGroup

TODO: validateOnLoad but feel like it shoul be moved to the formgroup layer
TODO: conditionally validate // now feel like with dynamic inptufieldstate dont need to check  node.show, remvoe api for if to validate, assume noValidate with validation object is empty,
TODO: if validation is passed in fallback to a default validation message based on validation key OR check that a corresponding message key exists

current inputDate, inputText etc, we are duplciating a lot of logic here also repeatedly importing the composables
implement runMode

-- future upgrades --
easier api (use factory createNode directly)
	- use schema to create form automatically as with other form libraries
	- 
Guiding principles
1. reduce amount of surface area for code so less chances for bugs to appear / more easily debuggable

2. ease in migration (minimal change to current form)

3. keep logic close to wherever is required, and remove complicated nesting/recursive logic, less moving around files easier to find stuff

4. fully and correctly typed

```

let resetState, setting _inputState etc be done automatically: DONE , through watch and computed

i need to ensure that applyDate only shows after applicationType for showing works: DONE

DONE now i need to make sure that dispatch works and for show i am able to access the state properly
pass default value down and be able to respond to input 
```

Inaccessible host: `wins_mock_aws' at port `4566'. This service may not be available in the `ap-southeast-1' region.
Error: Inaccessible host: `wins_mock_aws' at port `4566'. This service may not be available in the `ap-southeast-1' region.


Error while executing "/app/migrations/seeds/04-company-giro-qa.js" seed: Knex: Timeout acquiring a connection. The pool is probably full. Are you missing a .transacting(trx) call?
Error: Error while executing "/app/migrations/seeds/04-company-giro-qa.js" seed: Knex: Timeout acquiring a connection. The pool is probably full. Are you missing a .transacting(trx) call?
    at Seeder._waterfallBatch (/app/node_modules/knex/lib/migrations/seed/Seeder.js:118:23)
KnexTimeoutError: Knex: Timeout acquiring a connection. The pool is probably full. Are you missing a .transacting(trx) call?
    at Client_Oracledb.acquireConnection (/app/node_modules/knex/lib/client.js:312:26)
    at Runner.ensureConnection (/app/node_modules/knex/lib/execution/runner.js:287:28)
    at Runner.run (/app/node_modules/knex/lib/execution/runner.js:30:19)
    at Object.exports.seed (/app/migrations/seeds/04-company-giro-qa.js:4:18)
    at Seeder._waterfallBatch (/app/node_modules/knex/lib/migrations/seed/Seeder.js:115:9)
