<template>
  <EmployeeMangement />
</template>

<script>
import EmployeeMangement from "./components/EmployeeMangement.vue";

export default {
  name: "App",
  components: {
    EmployeeMangement,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

body {
  font-family: 'Inter', sans-serif;
  background-color: #f8fafc;
  color: #1e293b;
  margin: 0;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#app {
  min-height: 100vh;
}
</style>
