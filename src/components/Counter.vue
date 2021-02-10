<template>
  <div class="clock-container">
    <section class="text-header">
      <h1 class="text-comming">Esperanos muy pronto...</h1>
      <h2 class="podcast-title">Podcast</h2>
    </section>
    <section class="clock">
      <div>
        <p class="clock-number">{{ displayDays }}</p>
        <p class="clock-text">dias</p>
      </div>
      <span class="double-dot">:</span>
      <div>
        <p class="clock-number">{{ displayHours }}</p>
        <p class="clock-text">horas</p>
      </div>
      <span class="double-dot">:</span>
      <div>
        <p class="clock-number">{{ displayMinutes }}</p>
        <p class="clock-text">minutos</p>
      </div>
      <span class="double-dot">:</span>
      <div>
        <p class="clock-number">{{ displaySeconds }}</p>
        <p class="clock-text">segundos</p>
      </div>
    </section>
    <section class="analog-clock-container">
      <div class="analog-clock">
        <p class="letras">Relog</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      displayDays: 100,
      displayHours: 10,
      displayMinutes: 10,
      displaySeconds: 10,
    };
  },
  computed: {
    seconds() {
      return 1000
    },
    minutes() {
      return this.seconds * 60
    },
    hours() {
      return this.minutes * 60
    },
    days() {
      return this.hours * 24
    }
  },
  mounted () {
    this.showRemaining();
  },
  methods: {
    formatNum(num) {
      return num < 10 ? '0' + num : num
    },
    showRemaining() {
      const timer = setInterval(() => {
        const now = new Date()
        const end = new Date(2021, 5, 7, 10, 10, 10, 10)
        const distance = end.getTime() - now.getTime()

        if (distance < 0) {
          clearInterval(timer)
          return
        }

        const daysRes = Math.floor((distance / this.days))
        const hoursRes = Math.floor((distance % this.days) / this.hours)
        const minutesRes = Math.floor((distance % this.hours) / this.minutes)
        const secondsRes = Math.floor((distance % this.minutes) / this.seconds)

        // this.displayMinutes = minutesRes < 10 ? '0' + minutesRes : minutesRes
        // this.displaySeconds = secondsRes < 10 ? '0' + secondsRes : secondsRes
        // this.displayHours = hoursRes < 10 ? '0' + hoursRes : hoursRes
        // this.displayDays = daysRes < 10 ? '0' + daysRes : daysRes
        this.displayMinutes = this.formatNum(minutesRes)
        this.displaySeconds = this.formatNum(secondsRes)
        this.displayHours = this.formatNum(hoursRes)
        this.displayDays = this.formatNum(daysRes)
      }, 1000)
    }
  },
};
</script>

<style scoped>
p {
  margin: 0;
  text-align: center;
}

.clock-container {
  margin-top: 2rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.text-header {
  width: 100%;
  text-align: center;
}

.text-comming {
  font-size: 3.5rem;
  margin-top: 0.5rem;
  margin-bottom: 0.5rem;
}

.podcast-title {
  font-size: 3rem;
  margin-top: 0;
  color: var(--action-color);
  animation: blip 2s infinite;
  animation-direction: alternate;
}

.clock {
  width: 35%;
  display: flex;
  justify-content: space-evenly;
}

.clock-number {
  font-size: 2.8rem;
  filter: drop-shadow(1px 1px 6px);
}

.clock-text {
  font-size: 1.5rem;
  filter: drop-shadow(1px 1px 6px);
}

.double-dot {
  font-size: 2.5rem;
}

.analog-clock-container {
  width: 100%;
  margin-top: 5rem;
  display: flex;
  justify-content: center;
}

.analog-clock {
  width: 150px;
  height: 150px;
  background-color: var(--text-color);
  border-radius: 50%;
  transform: rotateY(0deg);
  animation: clock 5s infinite;
  animation-direction: alternate;
}

.letras {
  color: var(--alert-color);
}

@keyframes clock {
  0% {
    transform: rotateY(0);
  }
  100% {
    transform: rotateY(360deg);
  }
}

@keyframes blip {
  0% {
    filter: drop-shadow(0 0 0);
  }
  100% {
    filter: drop-shadow(1px 1px 6px);
  }
}

</style>