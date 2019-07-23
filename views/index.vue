<template>
  <div>
    <h1>首页</h1>
    <router-link to="/about">跳转到about</router-link>
    <div>{{count}}</div>
    <button @click="handleIncrement">+1</button>
    <button @click="handleDecrease">-1</button>
    <button @click="handleMore">+10</button>
    <div>{{list}}</div>
  </div>
</template>
<script>
export default {
  computed: {
    count() {
      return this.$store.state.count;
    },
    list() {
      return this.$store.state.list.filter(item => item < 10);
    }
  },
  methods: {
    handleIncrement() {
      this.$store.commit({
        type: "increment",
        count: 1
      });
    },
    handleDecrease() {
      this.$store.commit("decrease");
    },
    handleMore() {
      this.$store.commit({
        type: "increment",
        count: 10
      });
    }
  }
};
</script>