<template>
  <v-app id="inspire">
    <v-app-bar
      app
      shrink-on-scroll
    class="light-green lighten-4"
    >
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      
      <v-spacer></v-spacer>
      <v-btn elevation="2" class="new" v-on:click="getNewsRu">Новости</v-btn>
      <v-spacer></v-spacer>
      <v-btn elevation="2" class="new" v-on:click="getNewsGb">News (GB)</v-btn>
      <v-spacer></v-spacer>
      <v-btn elevation="2" class="new" v-on:click="getNewsUs">News (USA)</v-btn>
      <v-spacer></v-spacer>
      <v-btn elevation="2" class="new" v-on:click="getNewsGe">Die Nachrichten</v-btn>
      <v-spacer></v-spacer>
      <v-btn elevation="2" class="new" v-on:click="getNewsFr">Nouvelles</v-btn>
      
      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main class="light-green lighten-5">
      <v-container>
        <v-row>
          <v-col v-for="i in news"
            :key="i"
            cols="4">
            <v-card>
                <v-card-title>{{i.title}}</v-card-title>
                <v-card-text>{{i.description}}</v-card-text>
                <v-card-actions><a v-bind:href="i.url">Источник</a></v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
    export default {
        name: 'App',
        data() {
            return {
                news: {}
            }
        },
        methods: {
            getNewsRu() {
                this.axios
                .get("https://newsapi.org/v2/top-headlines?country=ru&apiKey=d7f41a32c26b4bbfb596d58b1a54c766")
                .then((response) => {this.news = response.data.articles})
            },
            getNewsUs() {
                this.axios
                .get("https://newsapi.org/v2/top-headlines?country=us&apiKey=d7f41a32c26b4bbfb596d58b1a54c766")
                .then((response) => {this.news = response.data.articles})
            },
            getNewsGb() {
                this.axios
                .get("https://newsapi.org/v2/top-headlines?country=gb&apiKey=d7f41a32c26b4bbfb596d58b1a54c766")
                .then((response) => {this.news = response.data.articles})
            },
            getNewsGe() {
                this.axios
                .get("https://newsapi.org/v2/top-headlines?country=de&apiKey=d7f41a32c26b4bbfb596d58b1a54c766")
                .then((response) => {this.news = response.data.articles})
            },
            getNewsFr() {
                this.axios
                .get("https://newsapi.org/v2/top-headlines?country=fr&apiKey=d7f41a32c26b4bbfb596d58b1a54c766")
                .then((response) => {this.news = response.data.articles})
            }
        },
        mounted() {
            this.getNewsRu();
        }
    }
</script>


<style>
    a {
        box-sizing: border-box;
        padding-left: 8px;
    }
    .new {
        margin-top: 40px;
    }
</style>