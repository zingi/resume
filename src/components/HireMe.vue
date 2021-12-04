<template>
  <section id="hire-me-container" class="animated-gradient-background">
    <h3>{{ t('hire-me') }}</h3>
    <p>{{ t('i-am-currently-in-paternity') }}</p>
  </section>
</template>

<script>
import { useI18n } from 'vue-i18n'
export default {
  name: 'HireMe',
  setup () {
    const { t } = useI18n()
    return { t }
  }
}
</script>
