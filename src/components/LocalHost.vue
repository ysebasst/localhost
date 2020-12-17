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
      <div class="card urls" v-for="(puerto, i) of puertos" :key="i">
        <a :href="'http://localhost' + puerto">localhost{{ puerto }}</a>
        <a :href="'http://' + urlMobile + puerto"
          >{{ urlMobile }}{{ puerto }}</a
        >
      </div>
      <h3 class="card">Url mobile</h3>
      <div class="config-mobile">
        <input
          class="card"
          type="text"
          placeholder="Ingrese url mobile"
          v-model="urlMobile"
          @keyup="cambiarUrlMobile"
        />
        <button class="card" @click="cambiarUrlMobile">Cambiar</button>
      </div>
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
      urlMobile: "192.168.0.11",
      puertos: ["", ":3000", ":4000", ":5000", ":5500", ":8000", ":8080"],
    };
  },
  created() {
    if (localStorage.getItem("urlMobile")) {
      this.urlMobile = localStorage.getItem("urlMobile");
    }
  },
  methods: {
    redireccionar(e) {
      if (e.key === "Enter" || e.target.textContent === "Ir") {
        location.href = this.url;
      }
    },
    cambiarUrlMobile(e) {
      if (e.key === "Enter" || e.target.textContent === "Cambiar") {
        localStorage.setItem("urlMobile", this.urlMobile);
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
}
.grid {
  padding: 1rem;
  max-width: 786px;
  margin: 0 auto;
  display: grid;
  align-items: center;
  gap: 1rem;
}
.grid h1,
.grid h3 {
  text-align: center;
}
.grid .search,
.grid .config-mobile {
  display: flex;
}
.grid input {
  flex: 1;
  outline: none;
  border: none;
}
.grid button {
  border: none;
  margin-left: 0.5rem;
  cursor: pointer;
  outline: none;
}
.urls {
  display: flex;
  justify-content: space-between;
}
.urls a {
  text-decoration: none;
  font-weight: bold;
}
</style>
