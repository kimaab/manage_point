<template>
  <form @submit.prevent="handleSubmit">
    <input v-model="user.id" placeholder="ID" required />
    <input v-model="user.pwd" placeholder="Password" required />
    <input v-model="user.name" placeholder="Name" required />
    <input v-model="user.email" placeholder="Email" required />
    <button type="submit">Add User</button>
  </form>
</template>

<script>
import api from '../api';

export default {
  data() {
    return {
      user: { id: '', pwd: '', name: '', email: '' }
    };
  },
  methods: {
    async handleSubmit() {
      try {
        await api.post('/users', this.user);
        this.$emit('user-added2');
        this.user = { id: '', pwd: '', name: '', email: '' };
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>
