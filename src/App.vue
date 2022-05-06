<template>
  <div id="app">
    <header-component />
    <main-component />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  width: 70%;
  margin: 0 auto;
}
.debug {
  border: 1px solid black;
}
</style>
