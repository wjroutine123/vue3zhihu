<template>
  <div>{{ msg }}的年龄{{ age }}</div>
  <button @click="add">+</button>
  <div>{{ double }}</div>
  <!-- 组件 -->
  <content-child :msg="msg" @change="showName">子组件</content-child>
</template>

<script>
import { computed, reactive, toRefs, watch } from "vue";
import contentChild from "./components/contentChild.vue";

export default {
  name: "App",
  // 组件
  components: {
    contentChild,
  },
  setup() {
    const state = reactive({
      msg: "王大盒",
      age: 18,
      // 计算属性
      double: computed(() => {
        return state.age * 2;
      }),
    });
    // 点击事件
    function add() {
      state.age += 1;
    }
    // 点击+ 监听年龄 newVal->监听对象,oldVal->回调函数,clean->用于重复使用清理异步事务
    watch(
      () => state.age,
      (newVal, oldVal, clean) => {
        console.log(state.age + "去年" + oldVal + "今年" + newVal);
        clean(() => {
          console.log("clean");
        });
      }
    );
    function showName(params) {
      // params 子组件向父组件传过来的值
      alert(params);
    }
    return { ...toRefs(state), add, showName };
  },
};
</script>

<style>
</style>
