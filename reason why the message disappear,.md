translation access en.json becomes a function
https://github.com/intlify/vite-plugin-vue-i18n
look under ### `forceStringify`
this is found by logging 
![[Pasted image 20230831163351.png]]but don't know why though, the setting is false and we didnt define it

but it turns out is not in the plugin, interpolate now requires a function:
https://vue-i18n.intlify.dev/guide/advanced/function.html
The messages written in message format syntax are compiled into message functions with Vue I18n message compiler. Message functions and caching mechanism to maximize performance gains.

import { createVNode, Text } from 'vue'

const messages = {
  en: {
    greeting: ({ type }) => type === 'vnode'
      ? createVNode(Text, null, 'hello', 0)
      : 'hello'
  }
}

