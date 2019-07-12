<template>
  <div class="home">
    <div>
  <b-jumbotron bg-variant="info" text-variant="white" border-variant="dark">
    <template slot="header">Movies information</template>

    <template slot="lead">
      This page will show all the movies playing today.
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
    return {};
  },
  mounted() {
    axios.get("https://www.omdbapi.com/?t=god%2Bfather&y=&plot=short&apikey=2ccc910c")
  }
};
</script>
