<template>
  <div id="app">
    <MainForm />
  </div>
</template>

<script>
import MainForm from "./components/MainForm.vue";

export default {
  name: "App",
  components: {
    MainForm,
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
}
body {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  background-color: rgb(102, 102, 102);
}
</style>
