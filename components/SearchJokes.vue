<template>
  <form @submit.prevent="onSearch">
    <input type="text" v-model="term" placeholder="Enter a joke to search" required>
    <input type="submit" value="Search Joke">
  </form>
</template>

<script>
export default {
  name: "SearchJokes",
  data() {
    return {
      term: ""
    };
  },
  methods: {
    onSearch() {
      this.$emit("takeSearchTerm", this.term);
      //reset the term
      this.term = "";
    }
  }
};
</script>

<style scoped>
</style>