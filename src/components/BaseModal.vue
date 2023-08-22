<template>
  <Transition name="modal-outer">
    <div
      v-show="props.modalActive"
      class="absolute w-full bg-black bg-opacity-30 h-screen top-0 left-0 flex justify-center px-8"
    >
      <Transition name="modal-inner">
        <div
          v-if="props.modalActive"
          class="p-4 bg-white self-start mt-32 max-w-screen-md"
        >
          <slot></slot>
          <button
            class="text-white mt-8 bg-weather-primary py-2 px-6"
            @click="$emit('close-modal')"
          >
            Close
          </button>
        </div>
      </Transition>
    </div>
  </Transition>
</template>

<script setup>
import { defineProps, defineEmits } from "vue";
defineEmits(["close-modal"]);
const props = defineProps({ modalActive: Boolean });
</script>

<style scoped>
.modal-outer-enter-active,
.modal-outer-leave-active {
  transition: opacity 0.5s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-outer-enter-from,
.modal-outer-leave-to {
  opacity: 0;
}
</style>
