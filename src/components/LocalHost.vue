<template>
  <div class="content">
    <div class="grid">
      <h1 class="card">Localhost</h1>
      <div class="search">
        <input
          class="card"
          type="url"
          placeholder="Ingrese url"
          v-model="url"
          @keyup="redireccionar"
        />
        <button class="card" @click="redireccionar">Ir</button>
      </div>
      <a class="card" href="http://localhost">localhost</a>
      <a class="card" href="http://localhost:3000">localhost:3000</a>
      <a class="card" href="http://localhost:4000">localhost:4000</a>
      <a class="card" href="http://localhost:5000">localhost:5000</a>
      <a class="card" href="http://localhost:5500">localhost:5500</a>
      <a class="card" href="http://localhost:8000">localhost:8000</a>
      <a class="card" href="http://localhost:8080">localhost:8080</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hora",
  props: {
    msg: String,
  },
  data() {
    return {
      url: "",
    };
  },
  methods: {
    redireccionar(e) {
      if (e.key === "Enter" || e.target.textContent === "Ir") {
        location.href = this.url;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.content {
  background-color: #555;
  color: #fff;
  min-height: 100vh;
  /* display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column; */
}
.grid {
  padding: 1rem;
  max-width: 786px;
  margin: 0 auto;
  display: grid;
  align-items: center;
  gap: 1rem;
}
.grid h1 {
  text-align: center;
}
.grid .search {
  display: flex;
}
.grid .search input {
  flex: 1;
  outline: none;
  border: none;
}
.grid .search button {
  border: none;
  margin-left: 0.5rem;
  cursor: pointer;
  outline: none;
}
</style>
