<template>
  <section id="general-info-container">
    <div class="key">{{ t('general-info.nationality') }}</div>
    <div>{{ t('general-info.italian') }}</div>

    <div class="key">{{ t('general-info.current-residence') }}</div>
    <div>{{ t('general-info.austria') }}</div>

    <div class="key">{{ t('general-info.age') }}</div>
    <div>{{ currentAge }}</div>

    <div class="key">{{ t('general-info.native-language') }}</div>
    <div>{{ t('general-info.german') }}</div>

    <div class="key">{{ t('general-info.other-languages') }}</div>
    <div>{{ t('general-info.english-italian') }}</div>

    <div class="key">{{ t('general-info.driving-license') }}</div>
    <div>{{ t('general-info.class-b') }}</div>

    <div class="key">{{ t('general-info.covid-vaccination') }}</div>
    <div>{{ t('general-info.three-shots') }}</div>
  </section>
</template>

<script>
import { useI18n } from 'vue-i18n'
import { DateTime, Interval } from 'luxon'
import { ref } from '@vue/reactivity'

export default {
  setup () {
    const { t } = useI18n()

    const getCurrentAge = () => {
      const birthDate = DateTime.utc(1996, 10, 7, 1, 43)
      const now = DateTime.utc()

      // create interval, from my birth date until now
      const yearsInterval = Interval.fromDateTimes(birthDate, now)
      // get integer number of years
      const years = Math.floor(yearsInterval.length('years'))

      // create interval of unfinished year
      const daysInterval = yearsInterval.splitAt(birthDate.plus({ years }))[1]
      // get whole number of days of unfinished year
      const days = Math.floor(daysInterval.length('days'))

      // create interval of unfinished day
      const hoursInterval = daysInterval.splitAt(birthDate.plus({ years, days })).length < 2
        ? daysInterval.splitAt(birthDate.plus({ years, days }))[0]
        : daysInterval.splitAt(birthDate.plus({ years, days }))[1]
      // get whole number of hours of unfinished day
      const hours = Math.floor(hoursInterval.length('hours'))

      // create interval of unfinished hour
      const minutesInterval = hoursInterval.splitAt(birthDate.plus({ years, days, hours })).length < 2
        ? hoursInterval.splitAt(birthDate.plus({ years, days, hours }))[0]
        : hoursInterval.splitAt(birthDate.plus({ years, days, hours }))[1]
      // get whole number of minutes of unfinished hour
      const minutes = Math.floor(minutesInterval.length('minutes'))

      // create interval of unfinished minute
      const secondsInterval = minutesInterval.splitAt(birthDate.plus({ years, days, hours, minutes })).length < 2
        ? minutesInterval.splitAt(birthDate.plus({ years, days, hours, minutes }))[0]
        : minutesInterval.splitAt(birthDate.plus({ years, days, hours, minutes }))[1]
      // get whole number of seconds of unfinished minute
      const seconds = Math.floor(secondsInterval.length('seconds'))

      const hoursString = `${hours}`.padStart(2, '0')
      const minutesString = `${minutes}`.padStart(2, '0')
      const secondsString = `${seconds}`.padStart(2, '0')

      return `${years}y ${days}d ${hoursString}h ${minutesString}m ${secondsString}s`
    }

    const currentAge = ref(getCurrentAge())

    setInterval(() => {
      currentAge.value = getCurrentAge()
    }, 1000)

    return { t, currentAge }
  }
}
</script>
