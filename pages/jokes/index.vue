<template>
  <div>
    <Joke v-for="joke in jokes" :key="joke.id" 
    :joke="joke.joke" :id="joke.id"/>
  </div>
</template>

<script>
import axios from "axios";
import Joke from "@/components/Joke";
export default {
  data() {
    return {
      jokes: []
    };
  },
  components: {
    Joke
  },
  async created() {
    const config = {
      headers: {
        Accept: "application/json"
      }
    };
    try {
      // Make the async call and fetch the list of all the jokes from the backend
      const response = await axios.get(
        "https://icanhazdadjoke.com/search",
        config
      );
      const { results: jokes } = response.data;
      // set the jokes
      this.jokes = jokes;
    } catch (ex) {
      console.log(ex);
    }
  },
  head() {
    return {
      // For SEO (this is because of the vue-meta package)
      title: "List of the Jokes that we have",
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
