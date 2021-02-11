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
        <div class="hour" :style="`transform: rotate(${rotateHours}deg)`"></div>
        <div class="min" :style="`transform: rotate(${rotateMinutes}deg)`"></div>
        <div class="sec" :style="`transform: rotate(${rotateSeconds}deg)`" ></div>
        <div class="point"></div>
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
      rotateSeconds: 0,
      rotateMinutes: 0,
      rotateHours: 0,
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
    this.showClock();
  },
  methods: {
    formatNum(num) {
      return num < 10 ? '0' + num : num
    },
    showClock() {
      const time = setInterval(()=>{
        const clock = new Date()
        this.rotateSeconds = clock.getSeconds() * 6
        this.rotateMinutes = clock.getMinutes() * 6
        this.rotateHours = clock.getHours() * 12
      }, 1000)
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
        this.displaySeconds = this.formatNum(secondsRes)
        this.displayMinutes = this.formatNum(minutesRes)
        this.displayHours = this.formatNum(hoursRes)
        this.displayDays = this.formatNum(daysRes)

        // this.rotateSeconds = this.displaySeconds * -6
        // this.rotateMinutes = this.displayMinutes * -6
        // this.rotateHours = (this.displayHours * -12) 
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
  border: 8px solid black;
  background-image: radial-gradient(var(--text-color), var(--secondary-color));
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  /* transform: rotateY(0deg);
  animation: clock 5s infinite;
  animation-direction: alternate; */
}

.hour,
.min,
.sec {
  position: absolute;
  border-radius: 5px;
  transform-origin: bottom;
}

.hour {
  background-color: var(--action-color);
  height: 50px;
  width: 5px;
  bottom: 210px;
}

.min {
  background-color: var(--action-color);
  height: 70px;
  width: 5px;
  bottom: 210px;
}

.sec {
  background-color: var(--support-color);
  height: 70px;
  width: 2px;
  bottom: 210px;
}

.point {
  position: absolute;
  background-color: black;
  height: 15px;
  width: 15px;
  border-radius: 50%;
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

@media screen and (max-width: 768px) {
  .hour {
    bottom: 130px;
  }

  .min {
    bottom: 130px;
  }

  .sec {
    bottom: 130px;
  }
}

</style>