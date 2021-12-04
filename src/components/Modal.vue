<template>
  <div
    @click.self="closeModal"
    class="fixed z-10 inset-0 overflow-y-auto bg-opacity-75 transition-opacity"
    :class="theme === 'light' ? 'bg-gray-200' : 'bg-gray-900'"
  >
    <div
      class="inline-block align-bottom rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
    >
      <div
        class="px-4 pt-5 pb-4 sm:p-6 sm:pb-4"
        :class="theme === 'light' ? 'bg-white' : 'bg-gray-900'"
      >
        <slot> 
            <!-- default content -->
            <p class="mt-3 text-center text-white text-base my-4">go on,... enter something!</p>
        </slot>
        <slot name="links"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["theme"],
  methods: {
    closeModal() {
      this.$emit("close")
    },
  },
}
</script>

<style lang="scss">
.modal {
  width: 480px;
}
</style>
