<template>
  <div>
    <h1>Welcome to the best Jokes application</h1>
  </div>
</template>

<script>
export default {
  head() {
    return {
      // For SEO (this is because of the vue-meta package)
      title: "Welcome to the Jokes Application",
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
