<template>
  <div>
    <img src="../assets/news-icon.png">
    <!-- <h1>Headline News</h1> -->
    <!-- <form v-on:submit.prevent='getNews()'>
        <input type="text" v-model='query' placeholder='Enter search string'>
    </form> -->
    <!-- <button v-on:click='getNews()'>Refresh</button> -->
    <div v-for="article in news" class="single-article">
      <!-- <h2 class='headline' v-bind:href=`{{ article.url }}` target='blank'>{{ article.title}}</h2> -->
      <a class='headline' v-bind:href="article.url" target='blank'>{{ article.title }}</a>
      <p>{{ article.description}}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'headlinenews',
    data() {
        return {
            news: []
        }
    },
    methods: {
        getNews() {
            // alert(query)
            // newsapi.org key: a5e89e589424439bba84ede8e3329eea
            // axios.get('http://images-api.nasa.gov/apod?api_key=24180c1d-9862-4dde-88f3-80ca7ba4a5b9&search?q=' + query +'&media_type=image').then(function(response) {
            axios.get('https://newsapi.org/v1/articles?source=techcrunch&apiKey=a5e89e589424439bba84ede8e3329eea').then((response) => {
                console.log(response.data.articles)
                this.news = response.data.articles
                // console.log(this.news[0].author)
            })
        }
    },
    created: function() {
        // axios.get('https://newsapi.org/v1/articles?source=techcrunch&apiKey=a5e89e589424439bba84ede8e3329eea').then((response) => {
        //     console.log(response.data.articles)
        //     this.news = response.data.articles
        //     console.log(this.news[0].author)
        // })
        return this.getNews();
    }
}
</script>

<style scoped>
.headline {
    font-family: Arial, Helvetica, sans-serif;
    text-decoration: none;
    font-size: 22px;
    font-weight: bold;
    color: black;
}
.single-article {
  padding: 20px;
  margin: 20px 0;
  box-sizing: border-box;
  background: #d9dde2;
  font-family: Courier New, Courier, monospace;
}
</style>

