<template>
  <div class="container">
    <AppHeader/>
    <nuxt />
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader";
export default {
  components: {
    AppHeader
  }
};
</script>


<style scoped>
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}
body {
  font-family: 'Roboto', sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  background: #f4f4f4;
}
a {
  text-decoration: none;
  color: #666;
}
ul {
  list-style: none;
}
.container {
  max-width: 800px;
  margin: 2rem auto;
  overflow: hidden;
  padding: 1rem 2rem;
  background: #fff;
}
</style>
