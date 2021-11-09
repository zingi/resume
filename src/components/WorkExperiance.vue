<template>
  <h2>{{ t('work-experiance.work-experiance')}}</h2>

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
            t('work-experiance.metgis.serverimplementation'),
            t('work-experiance.metgis.apis'),
            t('work-experiance.metgis.web'),
            t('work-experiance.metgis.geospatial-data'),
            t('work-experiance.metgis.docker'),
            t('work-experiance.metgis.automation'),
            t('work-experiance.metgis.database')
          ]
        },
        {
          title: 'Elektrisola',
          timePeriod: [
            '2019-07-08 -> 2019-09-06',
            '2019-07-08 -> 2019-09-06',
            '2019-02-04 -> 2019-02-28',
          `2018-02-05 -> 2018-02-23 (${t('work-experiance.internship')})`,
          `2017-07-10 -> 2017-09-15 (${t('work-experiance.internship')})`

          ],
          tasks: [
            t('work-experiance.elektrisola.java'),
            t('work-experiance.elektrisola.web'),
            t('work-experiance.elektrisola.database'),
            t('work-experiance.elektrisola.server-maintenance'),
            t('work-experiance.elektrisola.automation')
          ]
        },
        {
          title: `${t('work-experiance.dengg.engineer')}: Adolf Dengg`,
          timePeriod: [
          `${t('work-experiance.summer')} 2016  (${t('work-experiance.internship')})`,
          `${t('work-experiance.summer')} 2015  (${t('work-experiance.internship')})`
          ],
          tasks: [
            t('work-experiance.dengg.acad-civil')
          ]
        },
        {
          title: `${t('work-experiance.contech.internet-agency')}: Contech`,
          timePeriod: [
          `${t('work-experiance.summer')} 2014  (${t('work-experiance.internship')})`
          ],
          tasks: [
            t('work-experiance.contech.website-maintenance'),
            t('work-experiance.contech.photoshop')
          ]
        },
        {
          title: 'Value Added Reseller: Joachim Kerer',
          timePeriod: [
          `${t('work-experiance.summer')} 2013  (${t('work-experiance.internship')})`
          ],
          tasks: [
            t('work-experiance.kerer.network-maintenance'),
            t('work-experiance.kerer.server-maintenance')
          ]
        },
        {
          title: `${t('work-experiance.dengg.engineer')}: Adolf Dengg`,
          timePeriod: [
          `${t('work-experiance.summer')} 2012  (${t('work-experiance.internship')})`
          ],
          tasks: [
            t('work-experiance.dengg.autocad')
          ]
        }
      ]
    })

    return { t, listEntries }
  }
}
</script>
