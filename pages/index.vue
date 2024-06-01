<!-- components/CountdownTimer.vue -->
<template>
  <div id="back">
    <h1 class="text-center white--text pt-10">ມານັກເວລາຕອນຮັບປີໃຫມ່​ 2024</h1>
  <div class="d-flex justify-center">
    <div  class="wrapp d-flex py-16 justify-center" style="margin-top:90px; font-size:50px">
      <div class="mx-3 font-weight-bold" >
        <span id="days">{{ days }}</span> ວັນ
      </div>
      <div class="mx-3 font-weight-bold" >
        <span id="hours">{{ hours }}</span> ຊົ່ວໂມງ
      </div>
      <div class="mx-3 font-weight-bold" >
        <span id="minutes">{{ minutes }}</span> ນາທີ
      </div>
      <div class="mx-3 font-weight-bold" >
        <span id="seconds">{{ seconds }}</span> ວິນາທີ
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      targetDate: new Date("2024-01-01T00:00:00Z"),
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
      this.hours = Math.floor(
        (timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)
      );
      this.minutes = Math.floor(
        (timeDifference % (1000 * 60 * 60)) / (1000 * 60)
      );
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

<style>
* {
  font-family: "Noto Serif Lao";
}
#back{
  background: url("https://wallpaperaccess.com/full/1739043.jpg") no-repeat
    center center fixed !important;
  background-size: cover;
  width: 100%;
  height: 100vh;
}
.wrapp{
  background: transparent;
  border: 2px solid rgba(225, 225, 225, .2) ;
  backdrop-filter: blur(20px);
  box-shadow: 0,0,10px solid rgba(0,0,0, .2) ;
  color: white;
  border-radius: 10px;
  width: 70%;
}
</style>
