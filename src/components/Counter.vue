<template>
  <div>
    <section>
      <h1>Esperanos muy pronto...</h1>
      <h2>Podcast</h2>
    </section>
    <div>
      <div>
        <p>{{displayDays}}</p>
        <p>dias</p>
      </div>
      <span>:</span>
      <div>
        <p>{{displayHours}}</p>
        <p>horas</p>
      </div>
      <span>:</span>
      <div>
        <p>{{displayMinutes}}</p>
        <p>minutos</p>
      </div>
      <span>:</span>
      <div>
        <p>{{displaySeconds}}</p>
        <p>segundos</p>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Counter',
    data() {
      return {
        displayDays: 100,
        displayHours: 10,
        displayMinutes: 10,
        displaySeconds: 10,
      }
    },
    // computed: {
    //   seconds() {
    //     return 1000
    //   },
    //   minutes() {
    //     return this.seconds * 60
    //   },
    //   hours() {
    //     return this.minutes * 60
    //   },
    //   days() {
    //     return this.hours * 24
    //   }
    // },
    // mounted () {
    //   this.showRemaining();
    // },
    // methods: {
    //   formatNum(num) {
    //     return num < 10 ? '0' + num : num
    //   }, 
    //   showRemaining() {
    //     const timer = setInterval(() => {
    //       const now = new Date()
    //       const end = new Date(2021, 5, 7, 10, 10, 10, 10)
    //       const distance = end.getTime() - now.getTime()

    //       if (distance < 0) {
    //         clearInterval(timer)
    //         return
    //       }

    //       const daysRes = Math.floor((distance / this.days))
    //       const hoursRes = Math.floor((distance % this.days) / this.hours)
    //       const minutesRes = Math.floor((distance % this.hours) / this.minutes)
    //       const secondsRes = Math.floor((distance % this.minutes) / this.seconds)

    //       // this.displayMinutes = minutesRes < 10 ? '0' + minutesRes : minutesRes
    //       // this.displaySeconds = secondsRes < 10 ? '0' + secondsRes : secondsRes
    //       // this.displayHours = hoursRes < 10 ? '0' + hoursRes : hoursRes
    //       // this.displayDays = daysRes < 10 ? '0' + daysRes : daysRes 
    //       this.displayMinutes = this.formatNum(minutesRes)
    //       this.displaySeconds = this.formatNum(secondsRes)
    //       this.displayHours = this.formatNum(hoursRes)
    //       this.displayDays = this.formatNum(daysRes)
    //     }, 1000)
    //   }
    // },
  }
</script>

<style scoped>

</style>