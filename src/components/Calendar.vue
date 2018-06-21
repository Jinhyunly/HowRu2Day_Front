<template>
  <div class="Calendar">
    <div class="section">
        <div class="container" id="calendar_header">
        </div>
    </div>
    <div class="section">
        <div class="container" @click="num" id="calendar_calendar">
           <vue-event-calendar :events="demoEvents"  @day-changed="handleDayChanged" @month-changed="handleMonthChanged"></vue-event-calendar>
            <template scope="props">
              <div v-for="(event, index) in props.showEvents" class="event-item" v-bind:key="event, index">
                {{event}}
              </div>
          </template>
          {{number}}
        </div>
    </div>
  </div>
</template>

<script>
let today = new Date()
export default {
  name: 'calendar',
  data () {
    return {
      number: 0,
      demoEvents: [{
        date: `${today.getFullYear()}/${today.getMonth() + 1}/8}`,
        title: '♧',
        desc: '생리시작'
      },
      {
        date: `${today.getFullYear()}/${today.getMonth() + 1}/24`,
        title: '♣',
        desc: '생리끝'
      }
      ]
    }
  },
  methods: {
    handleDayChanged (data) {
      // alert(data)
    },
    handleMonthChanged (data) {
      // alert(data)
    },
    num (e) {
      if (e.target.className === 'date-num' && e.target.textContent > 0) {
        this.number = e.target.textContent
        var a = { date: `${today.getFullYear()}/${today.getMonth() + 1}/${this.number}`, title: 'fuck', desc: 'fucking' }
        this.demoEvents.push(a)
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

