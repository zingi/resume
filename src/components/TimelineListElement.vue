  <template>
  <section class="timelist-element">
    <div class="timeline-list-element-title-container">
      <h3> {{title}} </h3>
      <ul>
        <li class="time-period" v-for="(value, index) in timePeriod" :key="index"> {{value}} </li>
      </ul>
    </div>

    <!-- <br v-if="tasks.length > 0"/> -->

    <ul v-if="tasks.length > 0">
      <li v-for="(task, index) in tasks" :key="index">__ {{task}}</li>
    </ul>

  </section>
</template>

<script>
export default {
  name: 'TimelineListElement',
  props: {
    title: {
      type: String
    },
    timePeriod: {
      type: Array
    },
    tasks: {
      type: Array,
      default: function () { return [] }
    }
  },
  setup () {

  }
}
</script>

<style scoped>

li {
  list-style-type: none;
}

/* .timeline-list-element-title-container {
  display: grid;
  grid-template-rows: 1fr 1fr;
} */

</style>
