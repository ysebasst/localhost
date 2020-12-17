<template>
  <div id="app">
    <LocalHost msg="msg" />
  </div>
</template>

<script>
import LocalHost from "./components/LocalHost.vue";

export default {
  name: "App",
  components: {
    LocalHost,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.card {
  background-color: #fff;
  color: #000;
  border-radius: 0.5rem;
  overflow: hidden;
}
.card-header {
  padding: 1rem;
  background-color: #bbb;
}
.card-body {
  padding: 1rem;
}

a.card {
  text-decoration: none;
}
</style>
