<template>
  <div id="app">
    <NavBar />
    <div class="container">
      <div class="card card-body">
        <h1>Pesquisando usuario da plataforma github</h1>
        <p>Digite um nome para encontrar usuario ou repositorio</p>
        <input
          @keyup="getUser"
          id="search"
          type="text"
          class="form-control"
          required
        />
      </div>
      <div class="row mt-3" v-if="user.length !== 0">
        <div class="col-md-4">
          <profile :user="user" />
        </div>
        <div class="col-md-8">
          <repo v-for="repo in repos" :key="repo" :repo="repo" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import profile from "./components/Profile.vue";
import repo from "./components/Repo.vue";
import axios from "axios";
export default {
  name: "app",
  data() {
    return {
      github: {
        url: `https://api.github.com/users`,
        client_id: "",
        client_secret: "",
        count: 7,
        sort: "created: asc"
      },
      user: [],
      repos: []
    };
  },
  components: {
    NavBar,
    profile,
    repo
  },
  methods: {
    getUser(e) {
      const user = e.target.value;
      const { url } = this.github;
      axios.get(`${url}/${user}`).then(({ data }) => (this.user = data));
    }
  }
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
