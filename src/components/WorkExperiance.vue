<template>
  <h2>{{ t('work-experience.work-experience')}}</h2>

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
  name: 'WorkExperiance',
  setup () {
    const { t } = useI18n()

    /*
    use 'computed' here for reactiviy to work,
    when changing between languages
    */
    const listEntries = computed(() => {
      return [
        {
          title: 'MetGIS',
          timePeriod: ['2019-10-28 -> 2021-09-06'],
          tasks: [
            t('work-experience.metgis.serverimplementation'),
            t('work-experience.metgis.apis'),
            t('work-experience.metgis.web'),
            t('work-experience.metgis.geospatial-data'),
            t('work-experience.metgis.docker'),
            t('work-experience.metgis.automation'),
            t('work-experience.metgis.database')
          ]
        },
        {
          title: 'Elektrisola',
          timePeriod: [
            '2019-07-08 -> 2019-09-06',
            '2019-07-08 -> 2019-09-06',
            '2019-02-04 -> 2019-02-28',
          `2018-02-05 -> 2018-02-23 (${t('work-experience.internship')})`,
          `2017-07-10 -> 2017-09-15 (${t('work-experience.internship')})`

          ],
          tasks: [
            t('work-experience.elektrisola.java'),
            t('work-experience.elektrisola.web'),
            t('work-experience.elektrisola.database'),
            t('work-experience.elektrisola.server-maintenance'),
            t('work-experience.elektrisola.automation')
          ]
        },
        {
          title: `${t('work-experience.dengg.engineer')}: Adolf Dengg`,
          timePeriod: [
          `${t('work-experience.summer')} 2016  (${t('work-experience.internship')})`,
          `${t('work-experience.summer')} 2015  (${t('work-experience.internship')})`
          ],
          tasks: [
            t('work-experience.dengg.acad-civil')
          ]
        },
        {
          title: `${t('work-experience.contech.internet-agency')}: Contech`,
          timePeriod: [
          `${t('work-experience.summer')} 2014  (${t('work-experience.internship')})`
          ],
          tasks: [
            t('work-experience.contech.website-maintenance'),
            t('work-experience.contech.photoshop')
          ]
        },
        {
          title: 'Value Added Reseller: Joachim Kerer',
          timePeriod: [
          `${t('work-experience.summer')} 2013  (${t('work-experience.internship')})`
          ],
          tasks: [
            t('work-experience.kerer.network-maintenance'),
            t('work-experience.kerer.server-maintenance')
          ]
        },
        {
          title: `${t('work-experience.dengg.engineer')}: Adolf Dengg`,
          timePeriod: [
          `${t('work-experience.summer')} 2012  (${t('work-experience.internship')})`
          ],
          tasks: [
            t('work-experience.dengg.autocad')
          ]
        }
      ]
    })

    return { t, listEntries }
  }
}
</script>
