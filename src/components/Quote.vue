<template>
  <div>
    <p class="text">"{{quote}}"</p>
    <h5>{{author}}</h5>
    <button @click="getQuote()">Show</button>
  </div>
</template>

<script>
import axios from 'axios'
  
export default {
  name: 'Quote',
  
  data: () => {
    return {
      quote: '',
      author: ''
    }
  },
  methods: {
    async getQuote () {
      const randomQuoteApi = 'https://programming-quotes-api.herokuapp.com/quotes/random'
      const res = await axios.get(randomQuoteApi)
      this.quote = res.data.en
      this.author = res.data.author
    }
  },
  created:
    async function getQuote () {
      const randomQuoteApi = 'https://programming-quotes-api.herokuapp.com/quotes/random'
      const res = await axios.get(randomQuoteApi)
      this.quote = res.data.en
      this.author = res.data.author
    }
}
</script>

<style lang="scss" scoped>

</style>