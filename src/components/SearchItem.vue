<template>
  <div>{{keyword}}</div>
  <button @click="fanhui">返回</button>
</template>

<script>
export default {
  data() {
    return {
      keyword: this.$route.query.value,
    };
  },
  methods: {
    fanhui() {
      this.$router.push({ path: "/" });
    },
  },
  mounted() {},
};
</script>

<style>
</style>