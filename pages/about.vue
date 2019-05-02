<template>
  <div>
    <h1>About Jokes</h1>
    <p>This is an app that displays jokes that are fetched
      from an API
    </p>
  </div>
</template>

<script>
export default {
  head() {
    return {
      // For SEO (this is because of the vue-meta package)
      title: "About JokesApp",
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
