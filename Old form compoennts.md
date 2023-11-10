# Code Duplication and Size
Among the input components in the repository, the main difference lies in the specific input type they represent (e.g., text input, select input, checkbox input). However, they all share a common set of mixins that provide general input functionality such as dispatching, validation, and common logic.
They are also wrapped over with FormGroup for the display of validation message, labels or to group a set of inputs etc
mixins - common, dispatch, validation
- Each component would essentially have the same set of mixins and shared functionality, resulting in redundant code. This duplication increases the size of the codebase and makes it harder to maintain and update.
- Introducing redundant code makes the application slower and consumes more memory, the whole of common-form-component is consumed by the forms. tree-shaking does not apply to globally registered components, we are duplicating registering the design system base components and these wrapper components
- 
- to configure an input component differently would have to do so on common-form-components, abstract over the surface of the component and duplicating the props we have to pass in. Case in point -
- 

# Code tightly coupled to Vuex State management
- this reduces the reusability of the components in scenarios where a different state management solution is used or when Vuex is not needed
Notice on FormGroup.vue, FormFacilitator.vue, common.js
- this also presents the problem of ensuring the ui and vuex is synchronised (when repeated components)
![[Pasted image 20231109200520.png]]
Vuex does not have typescript integration available and has been replaced by Pinia as the official state management library Vue 3 onwards

# Form Library Documentation

### Introduction

  
This form library is a powerful tool for handling form-related tasks in Vue.js applications. It provides a set of components and helper functions that make it easier to create, validate, and manage forms. The library is designed to be flexible and extensible, allowing you to customize its behavior to suit your specific needs.  

### Components

#### FormFacilitatorV2

  
This is the main component of the library. It is responsible for defining the form's schema, managing its state, and handling form validation. It uses the initialiseForm helper function to set up the form's state, dispatchers, and validators based on the provided schema.  

#### FormRepeater

  
This component is used for handling forms that contain repeatable fields. It provides functionality for adding and removing fields dynamically. It also uses the processNestedSlotContent helper function to process nested slots, which is useful for handling complex form structures.  

### Helper Functions

#### initialiseForm

  
This function is used to initialize the form's state, dispatchers, and validators based on the provided schema. It uses the createFormState, getFormValidator, and createFormDispatchers helper functions to perform these tasks.  

#### processFormSlots

  
This function is used to process the form's slots. It handles the rendering of form inputs and manages their state and validation.  

#### processNestedSlotContent

  
This function is used to process nested slots in the form. It is particularly useful for handling complex form structures with nested fields.

### Benefits

  
1. Simplicity: The library provides a simple and intuitive API for handling forms. It abstracts away the complexity of form management, allowing you to focus on building your application.  
  
2. Flexibility: The library is designed to be flexible and extensible. You can customize its behavior to suit your specific needs.  
  
3. Reusability: The components and helper functions provided by the library are highly reusable. You can use them in different parts of your application, reducing code duplication and improving maintainability.  
  
4. Efficiency: The library provides efficient form handling mechanisms. It uses Vue's reactivity system to ensure that the form's state is always up-to-date, and it provides efficient validation mechanisms to ensure that your forms are always valid.  
  
5. Scalability: The library is designed to handle both simple and complex form structures. Whether you're building a simple contact form or a complex multi-step form, this library has got you covered.

## Examples of Usage

### FormFacilitatorV2

import FormFacilitatorV2 from '@/components/FormFacilitatorV2'

export default {

  components: {

    FormFacilitatorV2

  },

  data() {

    return {

      schema: {

        name: {

          type: String,

          required: true

        },

        email: {

          type: String,

          required: true

        }

      }

    }

  }

}

In your template:

<FormFacilitatorV2 :schema="schema">

  <!-- Your form fields go here -->

</FormFacilitatorV2>

### FormRepeater

import FormRepeater from '@/components/FormRepeater'

export default {

  components: {

    FormRepeater

  },

  data() {

    return {

      schema: {

        items: {

          type: Array,

          required: true,

          schema: {

            name: {

              type: String,

              required: true

            }

          }

        }

      }

    }

  }

}

In your template:

<FormRepeater :schema="schema.items">

  <!-- Your form fields go here -->

</FormRepeater>

  
In both examples, the schema prop is used to define the structure and validation rules of the form. The FormFacilitatorV2 and FormRepeater components handle the form's state and validation based on this schema.