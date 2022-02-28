<template>
  <div>{{ data }}</div>
  <button @click="changeName">
    通过按钮事件触发子组件的值向父组件传递的过程
  </button>
</template>

<script>
import { ref } from "vue";
export default {
  name: "contentChild",
  // 接收父组件传过来的数据
  props: {
    msg: String,
  },
  setup(props, context) {
    const data = ref(props.msg);
    // 子传父
    function changeName() {
      // 第一个是函数，第二个是要传的值
      context.emit("change", "Hello-哈哈哈哈");
    }
    return { data, changeName };
  },
};
</script>

<style>
</style>