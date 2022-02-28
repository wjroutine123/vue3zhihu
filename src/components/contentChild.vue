<template>
  <div>{{ data }}</div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "contentChild",
  // 接收父组件传过来的数据
  props: {
    msg: String,
  },
  setup(props) {
    const data = ref(props.msg);
    return { data };
  },
};
</script>

<style>
</style>