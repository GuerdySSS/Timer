<template>
  <div id="app" class="app">
    <div class="app__header">COUNTDOWN TO MY BIRTHDAY</div>
    <div class="app__timer">
      <div class="app__timer__block">
        <div class="app__timer__block__counter">{{days}}</div>
        <div class="app__timer__block__text">DAYS</div>
      </div>
      <div class="app__timer__block">
        <div class="app__timer__block__counter">{{hours}}</div>
        <div class="app__timer__block__text">HOURS</div>
      </div>
      <div class="app__timer__block">
        <div class="app__timer__block__counter">{{minutes}}</div>
        <div class="app__timer__block__text">MINUTES</div>
      </div>
      <div class="app__timer__block">
        <div class="app__timer__block__counter">{{seconds}}</div>
        <div class="app__timer__block__text">SECONDS</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      days: '',
      hours: '',
      minutes: '',
      seconds: ''
    }
  },
  mounted() {
    this.getTime()
  },
  methods: {
    getTime() {
      setInterval(() => {
        let myBirthay = new Date('2022-03-30T00:00:00.000').getTime()
      
        let delta = Math.floor((myBirthay - new Date()) / 1000);
        let days = Math.floor(delta / 86400);
        delta -= days * 86400;

        let hours = Math.floor(delta / 3600) % 24;
        delta -= hours * 3600;

        let minutes = Math.floor(delta / 60) % 60;
        delta -= minutes * 60;

        let seconds = delta % 60;

        this.days = days
        this.hours = hours
        this.minutes = minutes
        this.seconds = seconds
      }, 1000);
    }
  }
}
</script>
<style scoped lang="scss">
  @font-face {
      font-family: "Roboto";
      src: url("./fonts/Roboto-Light.ttf") format("truetype"); 
      font-style: normal; 
      font-weight: normal; 
  }

  .app {
    position: relative;
    top: 50%;
    transform: translateY(-50%);

    &__header {
      text-align: center;
      font-size: 50px;
    }

    &__timer {
      display: flex;
      justify-content: space-between;
      width: 700px;
      margin: 50 auto;

      &__block {
        text-align: center;

        &__counter {
          font-size: 90px;
        }

        &__text {
          font-size: 35px;
        }
      }
    }
  }
</style>