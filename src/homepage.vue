<template>
  <div class="home">
    <div v-for="result in results" :key="result.title">
      <p>title {{ result.title }}</p>
      <p>href {{ result.href }}</p>
      <p>ingredients {{ result.ingredients }}</p>
      <img :src="result.thumbnail" />
    </div>
  </div>
</template>

<script>
export default {
  name: "homepage",

  data() {
    return {
      results: {},
    };
  },
  beforeMount: function() {
    const app = this;

    const url =
      "https://noroffcors.herokuapp.com/http://www.recipepuppy.com/api/";

    fetch(url)
      .then(function(response) {
        console.log(response);
        return response.json();
      })
      .then(function(result) {
        app.results = result.results;
      })
      .catch(function(error) {
        console.log("api failed ERROR", error);
      });
  },
};
</script>
