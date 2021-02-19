<template>
  <teleport to="body"><!--有时候我们想把模板的内容移动到当前组件之外的DOM 中，可以使用teleport。to="body"表示把内容显示到body中-->
    <div class="model-bg" v-show="visible">
      <div class="model-content">
        <button class="close" @click="$emit('closeModel')">X</button>
        <div class="model-title">{{title}}</div>
        <div class="model-body">
          <slot>
            对话框ssss
          </slot>
        </div>
      </div>
    </div>
  </teleport>
</template>

<script>
export default {
  props: ["title", "visible"],
};
</script>

<style scoped>
.model-bg {
  background: #000;
  opacity: 0.7;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0px;
  left: 0px;
}
.model-content {
  width: 600px;
  min-height: 300px;
  border: 1px solid #eee;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #ffff;
}
.model-title {
  background: #eee;
  color: #000;
  height: 32px;
  line-height: 32px;
  text-align: left;
}
.model-body {
  padding: 40px;
  text-align: center;
}
.model-body {
  padding: 40px;
}
.close {
  position: absolute;
  right: 10px;
  top: 5px;
  padding: 5px;
  border: none;
  cursor: pointer;
}
</style>