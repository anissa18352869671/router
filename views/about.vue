<template>
  <div>
    <h1>介绍页</h1>
    <button @click="handleRouter">跳转到user</button>
    <div>{{list}}</div>
  </div>
</template>
<script>
export default {
  methods: {
    handleRouter() {
      this.$router.push("/user/123");
    }
  },
  computed: {
    list() {
      return this.$store.state.list.filter(item => item < 10);
    }
  }
};
</script>