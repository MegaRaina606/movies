<style scoped>
</style>

<template>

<div>
  <h6 style="color:red ">WELCOME </h6>
  <h5 style="color:blue"> HERE'S A COLLECTION OF MOVIES </h5>

  <input  style="width: 300px " type="text" placeholder="SEARCH YOUR FAVOURITE MOVIE"/>
  <div  style="width: 200px, display:block, color:green" v-for="movie in movies" :key="movie.id">
    <h5 style="color:blue"> Movie Title:{{ movie.title }}</h5>
    
    <h5 style="color:red">OVERVIEW : {{ movie.overview }}</h5>
    <img style="width: 200px,height:200px display:block" src="`public/assets/json/${movie.poster}`"  :alt="title">
  </div>
</div>

</template>

<script>
import axios from "axios";

export default {
  name: "home",
  mounted() {
    axios({
      method: "GET",
      url: "assets/json/movies.json",
    }).then(
      (response) => {
        this.movies = JSON.parse(JSON.stringify(response.data));
      },
      (error) => {
        // eslint-disable-next-line
        console.error(error);
      }
    );
  },
  data() {
    return {
      movies: [],
    };
  },
  components: {},
  methods: {},
};
</script>
