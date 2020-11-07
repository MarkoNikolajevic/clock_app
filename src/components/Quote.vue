<template>
  <div class="flex-grid">
    <div>
      <p class="text">"{{quote}}"</p>
      <h5>{{author}}</h5>
    </div>
    <button @click="getQuote()">
      <img src="../assets/icon-refresh.svg" alt="Refresh icon">
    </button>
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
.flex-grid {
  display: flex;
  justify-content: space-between;
}
button {
  background: none;
  border: none;
  width: 1.125rem;
  height: 1.125rem;
  cursor: pointer;
}
</style>