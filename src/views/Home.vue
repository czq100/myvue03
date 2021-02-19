<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <First msg="Welcome to Your Vue.js App" />

    <button @click="isVisible=true">弹出模态对话框</button>
    <Model @closeModel="isVisible = false" :visible="isVisible" title="第一个对话框">
      sssssssssssssssssss
    </Model>
  </div>
</template>

<script>
// @ is an alias to /src
import First from "@/components/First.vue";
import Model from "@/components/Model.vue";
export default {
  name: "Home",
  components: {
    First,
    Model,
  },
  methods: {},
  data() {
    return {
      isVisible: false,
    };
  },
};
</script>

<style scoped>
.home {
  position: relative;
}
</style>