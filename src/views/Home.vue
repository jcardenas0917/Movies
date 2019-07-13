<template>
  <div class="home">
    <div>
      <b-jumbotron bg-variant="info" text-variant="white" border-variant="dark">
        <template slot="header">Movie information</template>
        <p id = "message">Type the name of your favorite movie</p>
        <template>
          <form>
            <input type="text" v-model="movie.userInput" />
            <br />
            <button type="submit" class="btn btn-primary" @click.prevent="handleSubmit">Submit</button>
            <button type="clear" class="btn btn-primary clear" @click="clear">Clear</button>
            <div id = "movieInfo">
            <h2>{{ movie.title }}</h2>
            <p>{{ movie.actors }}</p>
            <p>{{ movie.awards }}</p>
            <p>{{ movie.year }}</p>
            <p>{{ movie.rated }}</p>
            <p>{{ movie.plot }}</p>
             <img :src = "movie.poster">
             
          </div>
          </form>
          
        </template>

        <hr class="my-4" />
      </b-jumbotron>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from "axios";
export default {
  data() {
    return {
      movie: {
        userInput: "",
        title:"",
        actors: "",
        awards:"",
        year:"",
        poster:"",
        plot:"",
        rated:"",
        key:"2ccc910c"
      }
    };
  },
  methods: {
    handleSubmit() {
      axios
        .get(
          "https://www.omdbapi.com/?t=" +
            this.movie.userInput +
            "&apikey=" + this.movie.key
        )
        .then(response => {
          console.log(response.data);
          this.movie.title = response.data.Title;
          this.movie.actors ="Cast: " + response.data.Actors;
          this.movie.awards =response.data.Awards;
          this.movie.year = "Year: " + response.data.Year;
          this.movie.plot = "Plot: " + response.data.Plot;
          this.movie.rated ="Rated: " + response.data.Rated;
          this.movie.poster = response.data.Poster;
          console.log(this.movie.poster)
        });
      console.log(this.movie.userInput);
    },
    clear(){
      this.movie.title = null;
      this.movie.actors = null;
      this.movie.awards = null;
      this.movie.year = null;
      this.movie.rated = null;
      this.movie.poster = null;
      this.movie.plot = null;

    }
  }
};
</script>

<style scoped>
#message{
  font-weight: bold;
}
</style>
