<template>
  <div class="content">
    <div class="grid">
      <div class="card">
        <h3 class="card-header">Url personalizada</h3>
        <div class="search card-body">
          <input
            type="url"
            placeholder="Ingrese url"
            v-model="url"
            @keyup="redireccionar"
          />
          <button @click="redireccionar">Ir</button>
        </div>
      </div>
      <div class="card">
        <h3 class="card-header">Url Network</h3>
        <div class="config-mobile card-body">
          <input
            type="text"
            placeholder="Ingrese url mobile"
            v-model="urlMobile"
            @keyup="cambiarUrlMobile"
          />
          <button @click="cambiarUrlMobile">
            Guardar
          </button>
        </div>
      </div>
      <div class="card">
        <h3 class="card-header">Url Local - Url Network</h3>
        <div class="card-body">
          <div class="urls" v-for="(puerto, i) of puertos" :key="i">
            <a :href="'http://localhost' + puerto">localhost{{ puerto }}</a>
            <a :href="'http://' + urlMobile + puerto"
              >{{ urlMobile }}{{ puerto }}</a
            >
          </div>
        </div>
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
      puertos: ["", ":3000", ":4000", ":4100", ":4200", ":4300", ":4400", ":4500", ":5000", ":5500", ":8000", ":8080"],
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
      if (e.key === "Enter" || e.target.textContent === "Guardar") {
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
  padding: 0.5rem 1rem;
}
.grid button {
  padding: 0.5rem 1rem;
  margin-left: 0.5rem;
  cursor: pointer;
  outline: none;
}
.urls {
  display: flex;
  justify-content: space-between;
  padding: 0.5rem 0;
  border-bottom: 1px solid #bbb;
}
.urls a {
  text-decoration: none;
  font-weight: bold;
  color: #333;
}
</style>
