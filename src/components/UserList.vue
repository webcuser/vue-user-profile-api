<template>
  <div>
    <h1>User Profiles</h1>
    <ul>
      <li v-for="user in users" :key="user.id">{{ user.name }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.fetchUsers();
  },
  methods: {
    async fetchUsers() {
      const response = await axios.get('http://localhost:3000/api/users');
      this.users = response.data;
    },
  },
};
</script>

<style scoped>
ul {
  list-style-type: none;
}
</style>