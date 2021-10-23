<template>
  <h2>{{ t('education.education') }}</h2>
  <timeline-list-element v-for="(entry,index) in listEntries" :key="index"
    :title="entry.title"
    :timePeriod="entry.timePeriod"
    :tasks="entry.tasks"
  ></timeline-list-element>
</template>

<script>
import { computed } from '@vue/reactivity'
import { useI18n } from 'vue-i18n'
import TimelineListElement from './TimelineListElement.vue'

export default {
  components: { TimelineListElement },
  setup () {
    const { t } = useI18n()

    const listEntries = computed(() => {
      return [
        {
          title: t('education.university'),
          timePeriod: ['2015 -> 2020']
        },
        {
          title: t('education.high-school'),
          timePeriod: ['2010 -> 2015']
        },
        {
          title: t('education.middle-school'),
          timePeriod: ['2007 -> 2010']
        }
      ]
    })

    return { t, listEntries }
  }
}
</script>
