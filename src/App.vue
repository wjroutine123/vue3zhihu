<template>
  <!--  <img alt="Vue logo" src="./assets/logo.png">-->
  <!--  <HelloWorld msg="Welcome to Your Vue.js App"/>-->
  <div>{{ msg }}的年龄{{ age }}</div>
  <button @click="add">+</button>
  <div>{{ double }}</div>
  <!-- 组件 -->
  <content-child></content-child>
</template>

<script>
import { computed, ref } from "vue";
import contentChild from "./components/contentChild.vue";

export default {
  name: "App",
// 组件
  components: {
    contentChild,
  },
  setup() {
    const msg = ref("王大盒");
    const age = ref(18);
// 计算属性
    const double = computed(() => {
      return age.value * 2;
    });
// 点击事件
    function add() {
      age.value += 1;
    }
    return { msg, age, add,double };
  },
};
</script>

<style>

</style>
