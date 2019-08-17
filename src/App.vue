<template>
  <div id="app">
    <div id="nav">
      <router-link :to="{ name: 'home' }">Home</router-link>
      <router-link v-if="!auth" :to="{ name: 'signup' }">Sign Up</router-link>
      <router-link v-if="!auth" :to="{ name: 'signin' }">Sign In</router-link>
      <router-link v-if="auth" :to="{ name: 'dashboard' }"
        >Dashboard</router-link
      >
      <a v-if="auth" class="logout" @click="logout">Logout</a>
    </div>
        <router-view />
  </div>
</template>
<script>
import {  mapActions, mapGetters } from "vuex";
export default {
  computed: {

    ...mapGetters({
      auth: "isAuthenticated"
    })
  },
  methods: {
    ...mapActions(["logout", "autoLogin"])
  },
  created() {
    this.autoLogin();
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  max-width: 1024px;
  margin: 0 auto;
}
#nav {
  padding: 30px;
  cursor: pointer;
  background-color: grey;
}
#nav a {
  font-weight: bold;
  color: black;
  border-right: 1px solid;
  padding: 0 10px;
}
#nav a:last-child {
  border: none;
}
#nav a.router-link-exact-active {
  color: tomato;
}
.error {
  background-color:grey;
  padding: 20px;
  color:tomato;
  cursor: pointer;
}
</style>
