<template>
  <h1 class="header">PokeDex</h1>
  <card />
</template>

<script>
import card from "./components/card";
export default {
  name: "App",
  components: {
    card,
  },
};
</script>

<style lang="scss">
@use './scss/globals';
</style>
