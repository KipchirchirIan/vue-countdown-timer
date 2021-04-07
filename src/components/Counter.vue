<template>
  <div class="d-flex justify-content-center align-items-center counter">
    <div class="p-3 text-center font-pacifico">
      {{ displayDays }}
      <span class="d-block">Days</span>
    </div>
    <span class="font-weight-bold">:</span>
    <div class="p-3 text-center font-pacifico">
      {{ displayHours }}
      <span class="d-block">Hours</span>
    </div>
    <span class="font-weight-bold">:</span>
    <div class="p-3 text-center font-pacifico">
      {{ displayMinutes }}
      <span class="d-block">Minutes</span>
    </div>
    <span class="font-weight-bold">:</span>
    <div class="p-3 text-center font-pacifico">
      {{ displaySeconds }}
      <span class="d-block">Seconds</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Counter",
  data() {
    return {
      displayDays: 0,
      displayHours: 0,
      displayMinutes: 0,
      displaySeconds: 0,
    };
  },
  computed: {
    seconds() {
      return 1000;
    },
    minutes() {
      return this.seconds * 60;
    },
    hours() {
      return this.minutes * 60;
    },
    days() {
      return this.hours * 24;
    },
  },
  mounted() {
    setInterval(this.displayTime, 1000);
  },
  methods: {
    displayTime() {
      const now = new Date();
      const future = new Date(2021, 11, 31, 23, 59, 59);
      let distance = future - now;

      let days = Math.floor(distance / this.days);
      let hours = Math.floor((distance % this.days) / this.hours);
      let minutes = Math.floor((distance % this.hours) / this.minutes);
      let seconds = Math.floor((distance % this.minutes) / this.seconds);

      this.displayDays = days < 10 ? "0" + days : days;
      this.displayHours = hours < 10 ? "0" + hours : hours;
      this.displayMinutes = minutes < 10 ? "0" + minutes : minutes;
      this.displaySeconds = seconds < 10 ? "0" + seconds : seconds;
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Pacifico&display=swap");

.counter {
  font-size: 2.2em;
}

.font-pacifico {
  font-family: "Pacifico", cursive;
}
</style>
