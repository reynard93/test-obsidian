# Code Duplication and Size
Among the input components in the repository, the main difference lies in the specific input type they represent (e.g., text input, select input, checkbox input). However, they all share a common set of mixins that provide general input functionality such as dispatching, validation, and common logic.
mixins - common, dispatch, validation
- Creating a new component for each input type is wasteful because it leads to unnecessary code duplication. Each component would essentially have the same set of mixins and shared functionality, resulting in redundant code. This duplication increases the size of the codebase and makes it harder to maintain and update.
- Introducing redundant code makes the application slower and consumes more memory, the whole of common-form-component is consumed by the forms. tree-shaking does not apply to globally registered components, we are duplicating registering the design system base components and these wrapper components

# Code tightly coupled to Vuex State management
- this reduces the reusability of the components in scenarios where a different state management solution is used or when Vuex is not needed
Notice on FormGroup.vue, FormFacilitator.vue, common.js

Vuex does not have typescript integration available and has been replaced by Pinia as the official state management library Vue 3 onwards