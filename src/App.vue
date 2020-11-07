<template>
  <div id="app">
    <picture v-if='hours >= 5 && hours < 18' class='app-bg-img'>
      <source media="(min-width: 1200px)" srcset="./assets/bg-image-daytime-desktop.jpg">
      <source media="(min-width: 768px)" srcset="./assets/bg-image-daytime-tablet.jpg">
      <img class='app-bg-img' src="./assets/bg-image-daytime-mobile.jpg" alt="river between trees">
    </picture>
    <picture v-else class='app-bg-img'>
      <source media="(min-width: 1200px)" srcset="./assets/bg-image-nighttime-desktop.jpg">
      <source media="(min-width: 768px)" srcset="./assets/bg-image-nighttime-tablet.jpg">
      <img class='app-bg-img' src="./assets/bg-image-nighttime-mobile.jpg" alt="sky full of stars">
    </picture>
    <div class="inside">
      <Quote />
      <main>
        <div class='greeting-container'>
          <img v-if='hours >= 5 && hours < 18' src="./assets/icon-sun.svg" alt="sun icon">
          <img v-else src="./assets/icon-moon.svg" alt="moon icon">
          <h4 class='heading4' v-if='hours >= 5 && hours < 12'>Good morning</h4>
          <h4 class='heading4' v-else-if='hours >= 12 && hours < 18'>Good afternoon</h4>
          <h4 class='heading4' v-else-if='hours >= 18 || hours < 5'>Good evening</h4>
        </div>
        <h1 class='heading1'>{{time}}<span class="timezone">{{abbreviation}}</span></h1>
        <h3 class='heading3'>In {{city}}, {{countryCode}}</h3>
      </main>
    </div>
  </div>
</template>

<script>
import Quote from './components/Quote.vue'

export default {
  name: 'App',
  components: {
    Quote
  },
  data () {
    return {
      city: '',
      countryCode: '',
      time: '',
      abbreviation: '',
      hours: null
    }
  },
  methods: {
  },
  created:
  async function getLocation() {
    const locationApi = 'https://freegeoip.app/json/'
    const res = await this.$http.get(locationApi)
    this.city = res.data.city
    this.countryCode = res.data.country_code
    
    const timeApi = `http://worldtimeapi.org/api/ip`
    const resTime = await this.$http.get(timeApi)
    const isoTime = resTime.data.datetime
    this.time = isoTime.substr(11, 5)
    this.abbreviation = resTime.data.abbreviation
    const hoursStr = this.time.substr(0, 2)
    this.hours = parseInt(hoursStr, 10)
  }
}
</script>

<style lang='scss'>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700&display=swap');

#app {
  position: relative;
  color: $white;
  font-family: 'Inter', sans-serif;
  height: 100vh;

  .app-bg-img  {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .inside {
    position: relative;
    background-color: rgba(0, 0, 0, 0.4);
    height: 100%;
    padding: 2rem 1.625rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    @media screen and (min-width: 48rem) {
      padding: 5rem 8rem 4rem 4rem;
    }

    @media screen and (min-width: 85rem) {
      padding: 3.5rem 5.75rem 6.125rem 10.25rem;
    }
  }

  .greeting-container {
    display: flex;

    img {
      width: 1.5rem;
      height: 1.5rem;
      margin-right: 1rem;
    }
  }
}
</style>
