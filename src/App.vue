<style scoped>

</style>

<template>
  <div class="dialog-example">
    <button
      type="button"
      @click="onClickShowDialogButton">
      Dialog 표시
    </button>
    <Dialog
      v-model:visible="isVisible">
      <template v-slot:title>
        제목
      </template>
      <template v-slot:content>
        내용
      </template>
    </Dialog>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import Dialog from './components/Dialog/index.vue';

export default defineComponent({
  components: {
    Dialog,
  },
  setup() {
    const isVisible = ref(false);
    const onClickShowDialogButton = () => {
      isVisible.value = true;
    };

    return {
      isVisible,
      onClickShowDialogButton,
    };
  },
});
</script>
