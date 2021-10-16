<template>
  <h1>> {{ shownString }}</h1>
</template>

<script>
import { ref } from '@vue/reactivity'
// import { onMounted } from '@vue/runtime-core'
// import wait from 'wait'

export default {
  name: 'Headline',
  setup (props, context) {
    // final headline string
    const titleString = './Aaron_Zingerle_BSc'
    // char used to simulate cursor
    const cursorChar = '█'
    // headline string which is currently shown
    const shownString = ref('')

    shownString.value = titleString + cursorChar

    /* onMounted(async () => {
      // start shown string with only cursor char
      shownString.value = cursorChar
      await wait(200)

      // simulate writing of headline string
      for (let i = 0; i < titleString.length; i++) {
        shownString.value = shownString.value.replace(cursorChar, titleString[i]) + cursorChar
        const randomWait = Math.floor(Math.random() * 150) + 10
        await wait(randomWait)
      }

      await wait(700)
      // remove cursor char as if enter would be pressed
      shownString.value = shownString.value.slice(0, -1)

      context.emit('ready')
    }) */

    return {
      shownString
    }
  }
}
</script>
