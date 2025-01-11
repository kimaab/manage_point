<template>
  <div>
    <h2>Point Limits</h2>
    <ul>
      <li v-for="limit in limits" :key="limit.limit_id">
        {{ limit.member_id }} - {{ limit.month_year }} - {{ limit.total_used_points }} points
      </li>
    </ul>
  </div>
</template>

<script>
import api from '../api';

export default {
  data() {
    return {
      limits: []
    };
  },
  methods: {
    async fetchLimits() {
      try {
        const response = await api.get('/point-limits');
        console.log(response.data)
        this.limits = response.data;
      } catch (error) {
        console.error(error);
      }
    }
  },
  created() {
    this.fetchLimits();
  }
};
</script>
