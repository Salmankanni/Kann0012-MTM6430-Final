<template>
  <div>
    <h1>Dashboard</h1>
    <p>Welcome to your dashboard {{ user.name }}</p>
    <p>Your login email is: {{ user.email }}</p>
    <form @submit.prevent="submitForm">
      <label for="name">Edit your name:</label>
      <input type="text" id="name" v-model="user.name" />
      <br />
      <input type="submit" value="Submit" />
      <label for="name">Edit your age:</label>
      <input type="text" id="name" v-model="user.age" />
      <br />
      <input type="submit" value="Submit" />
      <label for="name">Edit your city:</label>
      <input type="text" id="name" v-model="user.city" />
      <br />
      <input type="submit" value="Submit" />
      <label for="name">Edit your job:</label>
      <input type="text" id="name" v-model="user.job" />
      <br />
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>
<script>
import { mapActions, mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters({
      userData: "getUser"
    }),
    user() {
      return !this.userData ? false : this.userData;
    }
  },
  created() {
    this.getUserData();
  },
  methods: {
    ...mapActions(["fetchUser", "updateUser"]),
    getUserData() {
      let userEmail = localStorage.getItem("userEmail");
      this.fetchUser(userEmail);
    },
    submitForm() {
      this.updateUser();
    }
  }
};
</script>
<style>
  h1,p{
    text-align: center;
  }
</style>
