<template>
  <div>
    <h1>首页</h1>
    <router-link to="/about">跳转到about</router-link>
    <div>{{count}}</div>
    <button @click="handleIncrement">+1</button>
    <button @click="handleDecrease">-1</button>
    <button @click="handleMore">+10</button>
    <button @click="handleAction">Action +1</button>
    <button @click="handleAsync">Async +1</button>
    <div>{{list}}</div>
    <div>{{listCount}}</div>
  </div>
</template>
<script>
export default {
  computed: {
    count() {
      return this.$store.state.count;
    },
    list() {
      return this.$store.getters.filteredList;
    },
    listCount() {
      return this.$store.getters.listCount;
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
    },
    handleAction() {
      this.$store.dispatch("increment");
    },
    handleAsync() {
      this.$store.dispatch("asyncIncrement").then(() => {
        console.log(this.$store.state.count);
      });
    }
  }
};
</script>