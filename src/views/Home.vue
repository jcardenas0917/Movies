<template>
  <div class="home">
    <div>
  <b-jumbotron bg-variant="info" text-variant="white" border-variant="dark">
    <template slot="header">Movies information</template>

    <template slot="lead">
     <input v-model="movieInfo" placeholder="edit me">
     <br>
     <button onclick="alert('clicked')">Submit</button>
          <p>Message is: {{ movieInfo }}</p>
      
    </template>

    <hr class="my-4">

    <p>
    
    </p>
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
      movieInfo:"",
    };
  },
  mounted() {
    axios.get("https://www.omdbapi.com/?t=the matrix&apikey=2ccc910c")
    .then(response => {
      console.log(response.data);
      this.movieInfo = response.data.Actors;
    })
  }
};
// $("#add-movie").on("click", function(event) {
//         event.preventDefault();
//         // This line grabs the input from the textbox
//         var movie = $("#movie-input").val().trim();
//       mounted(movie)
//       });

</script>
