<template>
  <div>
    <h1>Single Joke {{joke.id}}</h1>
    <p>{{joke.joke}}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      joke: {}
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      const response = await axios.get(
        "https://icanhazdadjoke.com/j/" + this.$route.params.id,
        config
      );
      // console.log(response.data);
      const { data: joke } = response;
      console.log(joke);
      this.joke = joke;
    } catch (ex) {}
  }
};
</script>

<style scoped>
</style>