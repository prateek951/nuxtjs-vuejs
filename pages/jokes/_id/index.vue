<template>
  <div>
    <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
    <h1>Joke #{{joke.id}}</h1>
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
    } catch (ex) {
      console.log(ex);
    }
  },
  head() {
    return {
      // For SEO (this is because of the vue-meta package)
      title: `Joke #${this.$route.params.id}`,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Best place for jokes app"
        }
      ]
    };
  }
};
</script>

<style scoped>
</style>