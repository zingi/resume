<template>
  <section id="contact-container">
    <h2>{{ t('contact') }}</h2>
    <p>{{ buttonDesc }}<button id="m-button">{{ buttonText }}</button></p>

    <div id="links">
      <a href="https://stackoverflow.com/users/9135945/zingi" target="blank">
        <img src="../assets/logos/stackoverflow.svg" alt="Stackoverflow">
      </a>
      <a href="https://github.com/zingi" target="blank">
        <img src="../assets/logos/github.svg" alt="GitHub" class="logo">
      </a>
      <a href="https://www.linkedin.com/in/aaron-z-3b750321b" target="blank">
        <img src="../assets/logos/linkedin.svg" alt="LinkedIn" id="linkedin-logo">
      </a>
    </div>

  </section>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import { useI18n } from 'vue-i18n'
export default {
  setup () {
    onMounted(() => {
      // add handler for m button clicked
      const mButton = document.getElementById('m-button')
      mButton.addEventListener('click', () => {
        // create link element
        const linkElement = document.createElement('a')
        // set href
        const arr = new Uint8Array([109, 97, 105, 108, 116, 111, 58, 104, 105, 114, 101, 45, 97, 97, 114, 111, 110, 64, 122, 105, 110, 103, 105, 46, 100, 101, 118])
        linkElement.href = Buffer.from(arr).toString('ascii')
        // trigger click
        linkElement.click()
      })
    })

    // text on m button
    const buttonText = Buffer.from(new Uint8Array([104, 105, 114, 101, 45, 97, 97, 114, 111, 110, 32, 91, 32, 65, 132, 84, 32, 93, 32, 122, 105, 110, 103, 105, 46, 100, 101, 118])).toString('ascii')
    // text before m button
    const buttonDesc = Buffer.from(new Uint8Array([69, 45, 77, 97, 105, 108, 58, 32])).toString('ascii')

    const { t } = useI18n()
    return { t, buttonText, buttonDesc }
  }
}
</script>
