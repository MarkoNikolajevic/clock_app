<template>
  <div id="app">
    <div class="inside">
      <Quote />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Quote from './components/Quote.vue'

const timeApi = 'http://worldtimeapi.org/api/timezone'
const locationApi = 'https://freegeoip.app/json/'

axios
  .get(timeApi)
  .then(response => (console.log(response)))

axios
  .get(locationApi)
  .then(response => (console.log(response.data.city)))


export default {
  name: 'App',
  components: {
    Quote
  },
  data () {
    return {
      quote: ''
    }
  },
  methods: {
    getQuote: function () {
      const randomQuoteApi = 'https://programming-quotes-api.herokuapp.com/quotes/random'
      axios
        .get(randomQuoteApi)
        .then((res) => {
          this.quote = res.data
          console.log(this.quote)
        })
    }
  }
}
</script>

<style lang='scss'>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');

*,
*::before,
*::after {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  position: relative;
  color: $white;
  font-family: 'Inter', sans-serif;
  height: 100vh;

  &::before {
    content: "";
    position: absolute;
    top: 0; left: 0;
    width: 100%; height: 100%;
    background: url('./assets/bg-image-daytime-mobile.jpg') no-repeat center center;
  }

  .inside {
    position: relative;
    background-color: rgba(0,0,0, 40%);
    height: 100%;
    padding: 2rem 1.625rem;
  }
}
</style>
