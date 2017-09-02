<template>
  <div>
    <img src="../assets/news-icon.png">
    <div v-for="article in news" class="single-article">
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
            axios.get('https://newsapi.org/v1/articles?source=techcrunch&apiKey=a5e89e589424439bba84ede8e3329eea').then((response) => {
                console.log(response.data.articles)
                this.news = response.data.articles
            })
        }
    },
    created: function() {
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

