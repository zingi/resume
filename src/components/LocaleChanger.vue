<template>
  <section class="locales">
    <button v-for="(lang, index) in locales" :key="index" :class="{ active: lang === activeLocal }" @click="setLocale(lang)">
      {{lang}}
    </button>
  </section>
</template>

<script>
import { useI18n } from 'vue-i18n'

export default {
  name: 'LocaleChange',
  setup () {
    const i18n = useI18n()
    const locales = ['en', 'de']
    const activeLocal = i18n.locale

    const setLocale = lang => {
      i18n.locale.value = lang
    }

    const currentLocale = i18n.locale.value

    return {
      locales,
      currentLocale,
      activeLocal,
      setLocale
    }
  }
}
</script>

<style scoped>

.locales button:not(:first-child) {
  margin-left: 1rem;
}

.active {
  text-decoration: underline;
}

</style>
