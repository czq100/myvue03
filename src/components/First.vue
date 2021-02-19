<template>
  <div @click="getIndustry">ssssssssssss</div>
  <span>{{msg}}</span>
  <br />
  <input type="text" v-model="keyword" @keyup="getIndustry2" />
  <ul>
    <li v-for="(item,index) in list" :key="index">
      <router-link :to="`/searchitem?value=${encodeURIComponent(item.q)}`">{{item.q}}</router-link>
    </li>
  </ul>
</template>

<script>
import fetchjsonp from "fetch-jsonp";
export default {
  props: {
    msg: {
      type: String,
    },
  },
  data() {
    return {
      keyword: "",
      list: [],
      timer: "",
    };
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
    getIndustry2() {
      //debugger;
      if (!this.keyword || !this.keyword.trim()) {
        return;
      }

      clearTimeout(this.timer);
      this.timer = setTimeout(() => {
        var _url =
          "https://www.baidu.com/sugrec?prod=pc&wd=" +
          encodeURIComponent(this.keyword);
        fetchjsonp(_url, { timeout: 5000, jsonpCallback: "cb" })
          .then((resp) => {
            return resp.json();
          })
          .then((data) => {
            console.log(data);
            this.list = data.g;
          })
          .catch((error) => {
            console.error(error);
          });
      }, 500);
    },
  },
};
</script>

<style>
</style>