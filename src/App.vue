<template>
  <div class="w-10/12 sm:w-8/12 md:w-6/12 lg:w-4/12 max max-w-lg mx-auto">
    <Home />
  </div>
</template>

<script>
import Home from "./components/Home.vue";
export default {
  name: "App",
  components: {
    Home,
  },
};
</script>
