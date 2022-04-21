<style scoped>
  .dialog__bg {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    pointer-events: none;
    z-index: 10;
  }
  .dialog__bg.dialog__bg--active {
    background-color: rgba(0, 0, 0, .4);
    pointer-events: inherit;
  }
  .dialog__content {
    border-radius: 4px;
    background-color: #FFF;
    max-width: 500px;
    width: 100%;
    position: fixed;
    right: 50%;
    top: 50%;
    transform: translate(50%, -50%);
    z-index: 11;
  }
  .dialog__content .dialog-title {
    padding: 16px;
    font-weight: bold;
    font-size: 21px;
  }
  .dialog__content .dialog-content {
    padding: 16px;
    padding-top: 0;
    font-size: 14px;
  }
</style>

<template>
  <div
    v-if="visible"
    class="dialog"
  >
    <teleport to='body'>
      <div
        :class="{ 'dialog__bg': true, 'dialog__bg--active': visible }"
        @click="onClickModal" />
    </teleport>
    <div class="dialog__content">
      <div class="dialog-title">
        <slot name="title"></slot>
      </div>
      <div class="dialog-content">
        <slot name="content"></slot>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

export default defineComponent({
  props: {
    visible: {
      type: Boolean as PropType<boolean>,
      required: false,
      default: false,
    },
  },
  setup(props, { emit }) {
    const onClickModal = () => {
      emit('update:visible');
    };
    return {
      onClickModal,
    };
  },
});
</script>
