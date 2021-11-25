<template>
  <div class="home">
    <h1>All Users</h1>
    <div v-for="user in users" v-bind:key="user.id">
      <h2>{{ user.name }}</h2>
      <img v-bind:src="user.url" v-bind:alt="user.name" />
      <p>Width: {{ user.width }}</p>
      <p>Height: {{ user.height }}</p>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      users: [],
    };
  },
  created: function () {
    this.indexUser();
  },
  methods: {
    indexUser: function () {
      axios.get("/users").then((response) => {
        console.log("users index", response);
        this.users = response.data;
      });
    },
  },
};
</script>
