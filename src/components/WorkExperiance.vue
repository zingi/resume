<template>
  <h2>{{ t('work-experiance')}}</h2>

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
  name: 'WorkExperiance',
  setup () {
    const { t } = useI18n()

    const listEntries = [
      {
        title: 'MetGIS',
        timePeriod: ['2019-10-28 -> 2021-09-06'],
        tasks: [t('server-implementation'), t('docker')]
      },
      {
        title: 'Elektrisola',
        timePeriod: [
          '2019-07-08 -> 2019-09-06',
          '2019-07-08 -> 2019-09-06',
          '2019-02-04 -> 2019-02-28',
          '2018-02-05 -> 2018-02-23 (Internship)',
          '2017-07-10 -> 2017-09-15 (Internship)'

        ],
        tasks: [
          'Java: Client/Server Anwendung mit REST',
          'HTML, CSS, Javascript, Vue.js, SQL',
          'Serverwartung',
          'Docker',
          'Automatisierung'
        ]
      }
    ]

    return { t, listEntries }
  }
}
</script>
