<template>
  <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" />
  <div style="width:300px; height:300px">
  <slot name="footer"></slot>
  </div>
  
</template>

<script lang="ts">
import { defineComponent } from "vue";
import HelloWorld from "../components/HelloWorld.vue";

export default defineComponent({
  name: "App",
  components: {
    HelloWorld,
  },
  props: {
    value: {
      type: [String, Number],
      default: "",
    },
    max: {
      type: Number,
      default: 99,
    },
    isDot: Boolean,
    hidden: Boolean,
    type: {
      type: String,
      default: "primary",
      validator: (val: string) => {
        return ["primary", "success", "warning", "info", "danger"].includes(
          val
        );
      },
    },
  },
  emits: {
    // 没有验证函数
    click: null,

    // 带有验证函数
    submit: (payload: any) => {
      if (payload.email && payload.password) {
        return true;
      } else {
        console.warn(`Invalid submit event payload!`);
        return false;
      }
    },
  },
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
