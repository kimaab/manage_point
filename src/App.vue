<template>
  <div id="app">
    <h1>Point Management System</h1>
    <UserForm @user-added="fetchUsers" />
    <UserList ref="userList" />
    <PointTransactionForm @transaction-added="fetchTransactions" />
    <PointTransactionList ref="transactionList" />
    <PointLimitList />
  </div>
</template>

<script>
import UserForm from './components/UserForm.vue';
import UserList from './components/UserList.vue';
import PointTransactionForm from './components/PointTransactionForm.vue';
import PointTransactionList from './components/PointTransactionList.vue';
import PointLimitList from './components/PointLimitList.vue';

export default {
  components: {
    UserForm,
    UserList,
    PointTransactionForm,
    PointTransactionList,
    PointLimitList,
  },
  methods: {
    fetchUsers() {
      this.$refs.userList.fetchUsers();
    },
    fetchTransactions() {
      this.$refs.transactionList.fetchTransactions();
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
