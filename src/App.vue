<template>
  <div id="app">
    <TheHeader />
    <router-view />
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";

export default {
  components: {
    TheHeader
  }
};
</script>
<style>
h1,
h2,
p,
h4 {
  font-family: "Exo 2", sans-serif;
}
</style>
