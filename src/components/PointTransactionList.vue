<template>
  <div>
    <h2>Point Transactions</h2>
    <ul>
      <li v-for="transaction in transactions" :key="transaction.transaction_id">
        {{ transaction.member_id }} - {{ transaction.transaction_type }} - {{ transaction.points }} points - {{ transaction.transaction_date }}
      </li>
    </ul>
  </div>
</template>

<script>
import api from '../api';

export default {
  data() {
    return {
      transactions: []
    };
  },
  methods: {
    async fetchTransactions() {
      try {
        const response = await api.get('/points');
        this.transactions = response.data;
      } catch (error) {
        console.error(error);
      }
    }
  },
  created() {
    this.fetchTransactions();
  }
};
</script>
