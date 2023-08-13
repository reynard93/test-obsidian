  <div id="overlay" class="portal" />
  <div id="overlay" class="portal" />
  <div id="overlay" class="portal" />
  <div id="overlay" class="portal" />
<div id="overlay" class="portal" /> 

<div id="overlay" class="portal" />

testing library code you defo want to test your types
https://www.totaltypescript.com/how-to-test-your-types

use assertType and expectTypeOf from vitest
expectTypeOf(mount).toBeFunction();

expectTypeOf(mount).parameter(0).toMatchTypeOf<{ name: string }>();

https://www.totaltypescript.com/testing-with-typescript-is-painful-heres-a-solution

// hopefully my any rules dont apply to tests
