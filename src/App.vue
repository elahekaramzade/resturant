<template>
  <div id="app">
    <Header />
    <Categories @passcurrentFilter="currentFilter = $event" />
    <Foods :currentFilter="currentFilter" @passCount="orderedFood = $event" />
    <Footer :orderedFood="orderedFood" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Categories from "./components/Categories";
import Footer from "./components/Footer";
import Foods from "./components/Foods";
export default {
  name: "App",
  components: {
    Header,
    Categories,
    Footer,
    Foods
  },
  data() {
    return {
      currentFilter: "",
      orderedFood: []
    };
  }
};
</script>

<style>
</style>
