<template>
  <button type="button" :class="classes" @click="onClick" :style="style">
    {{ label }}   
  </button>
</template>

<script>
import { reactive, computed } from "vue";

export default {
  name: "my-button",

  props: {
    label: {
      type: String,
      required: true,
    },
    primary: {
      type: Boolean,
      default: false,
    },
    backgroundColor: {
      type: String,
    },
  },

  emits: ["click"],

  setup(props, { emit }) {
    props = reactive(props);
    return {
      classes: computed(() => ({
        "storybook-button": true,
        "storybook-button--primary": props.primary,
      })),
      style: computed(() => ({
        backgroundColor: props.backgroundColor,
      })),
      onClick() {
        emit("click");
      },
    };
  },
};
</script>

<style>
.storybook-button {
  font: var(--textStylePSemiBoldBig);
  border: 0;
  border-radius: 3em;
  cursor: pointer;
  display: inline-block;
  background: var(--colorPrimary100);
  line-height: 1;
}
.storybook-button--primary {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  width: 365px;
  height: 60px;
  padding: 14px 23px;
  border-radius: 5px;
  background: var(--colorPrimary100);
  font: var(--textStylePSemiBoldBig);
  color: var(--colorTextWhite);
} 
.storybook-button--primary:hover{
  background: var(--colorPrimary200);
}
.storybook-button--primary:active {
  background: var(--colorPrimary300);
}

</style>
