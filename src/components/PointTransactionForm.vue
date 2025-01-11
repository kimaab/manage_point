<template>
  <form @submit.prevent="handleSubmit">
    <input v-model="transaction.member_id" placeholder="Member ID" required />
    <select v-model="transaction.transaction_type">
      <option value="earn">Earn</option>
      <option value="use">Use</option>
    </select>
    <input v-model="transaction.points" type="number" placeholder="Points" required />
    <input v-model="transaction.transaction_date" type="date" required />
    <button type="submit">Add Transaction</button>
  </form>
</template>

<script>
import api from '../api';

export default {
  data() {
    return {
      transaction: { member_id: '', transaction_type: 'earn', points: 0, transaction_date: '' }
    };
  },
  methods: {
    async handleSubmit() {
      try {
        await api.post('/points', this.transaction);
        this.$emit('transaction-added');
        this.transaction = { member_id: '', transaction_type: 'earn', points: 0, transaction_date: '' };
      } catch (error) {
        console.error(error);
      }
    }
  }
};
</script>
