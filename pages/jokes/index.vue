<template>
  <div>
    <SearchJokes @takeSearchTerm="onFilterJokes"/>
    <Joke v-for="joke in jokes" :key="joke.id" 
    :joke="joke.joke" :id="joke.id"/>
  </div>
</template>

<script>
import axios from "axios";
import Joke from "@/components/Joke";
import SearchJokes from "@/components/SearchJokes";
export default {
  data() {
    return {
      jokes: []
    };
  },
  components: {
    Joke,
    SearchJokes
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
  methods: {
    // Filter the jokes on the clientside
    onFilterJokes(data) {
      this.jokes = this.jokes.filter(joke => {
        if (joke.joke.includes(data)) {
          return joke;
        }
      });
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
