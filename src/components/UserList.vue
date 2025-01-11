<template>
  <div>
    <h2>User List</h2>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }} - {{ user.email }}
        <button @click="handleDelete(user.id)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
import api from '../api';

export default {
  data() {
    return {
      users: []
    };
  },
  methods: {
    async fetchUsers() {
      try {
        const response = await api.get('/users');
        this.users = response.data;
      } catch (error) {
        console.error(error);
      }
    },
    async handleDelete(id) {
      try {
        await api.delete(`/users/${id}`);
        this.fetchUsers();
      } catch (error) {
        console.error(error);
      }
    }
  },
  created() {
    this.fetchUsers();
  }
};
</script>
