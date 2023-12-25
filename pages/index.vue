<!-- components/CountdownTimer.vue -->
<template>
  <div>
    <h1>Countdown to 2024</h1>
    <div>
      <span id="days">{{ days }}</span> days
      <span id="hours">{{ hours }}</span> hours
      <span id="minutes">{{ minutes }}</span> minutes
      <span id="seconds">{{ seconds }}</span> seconds
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      targetDate: new Date('2024-01-01T00:00:00Z'),
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
    };
  },
  methods: {
    updateCountdown() {
      const currentDate = new Date();
      const timeDifference = this.targetDate - currentDate;

      this.days = Math.floor(timeDifference / (1000 * 60 * 60 * 24));
      this.hours = Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      this.minutes = Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60));
      this.seconds = Math.floor((timeDifference % (1000 * 60)) / 1000);
    },
  },
  mounted() {
    // Update the countdown every second
    this.updateCountdownInterval = setInterval(this.updateCountdown, 1000);
    // Initial update
    this.updateCountdown();
  },
  beforeDestroy() {
    // Clear the interval when the component is destroyed
    clearInterval(this.updateCountdownInterval);
  },
};
</script>
