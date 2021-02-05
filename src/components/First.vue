<template>
  <div @click="getIndustry">ssssssssssss</div>
  <span>{{msg}}</span>
</template>

<script>

export default {
  props: {
    msg: {
      type: String,
    },
  },
  methods: {
    getIndustry() {
      var _url =
        "http://api.open.zhaopin.com/dict/dictService/getItemList?access_token=c4215a32bbf74a2aa410db8473a58f4dV8k5&dictName=industry_relation&sceneName=";
      this.axios
        .get(_url)
        .then((resp) => {
          console.log(resp);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style>
</style>