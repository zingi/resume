<template>
  <h2>{{ t('education') }}</h2>
  <timeline-list-element v-for="(entry,index) in listEntries" :key="index"
    :title="entry.title"
    :timePeriod="entry.timePeriod"
    :tasks="entry.tasks"
  ></timeline-list-element>
</template>

<script>
import { useI18n } from 'vue-i18n'
import TimelineListElement from './TimelineListElement.vue'

export default {
  components: { TimelineListElement },
  setup () {
    const { t } = useI18n()

    const listEntries = [
      {
        title: 'BSc Media Informatics and Visual Computing - TU Wien',
        timePeriod: ['2015 -> 2020']
      },
      {
        title: 'Technologische Fachoberschule mit Fachrichtung Informatik',
        timePeriod: ['2010 -> 2015']
      }
    ]

    return { t, listEntries }
  }
}
</script>
