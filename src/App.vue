<template>
  <div class="text-center">
    <h1 class="text-6xl font-light text-center">{{ title }}</h1>
    <p class="text-2xl my-6 text-gray-500 font-light">Click buttons to display modals... ?</p>
    
    <teleport to=".modals" v-if="showModal">
      <Modal :theme=theme @close="toggleModal">
        
        <!-- named slot -->
        <template v-slot:links>
          <div class="text-center my-4 py-3">
            <a class="mx-2 rounded-md bg-blue-500 hover:bg-blue-800 transition duration-200 text-white p-4 text-xl" href="#">sign up now</a>
            <a class="mx-2 rounded-md bg-blue-500 hover:bg-blue-800 transition duration-200 text-white p-4 text-xl" href="#">more info</a>
          </div>
        </template>
        
        <!-- unnamed slot -->
        <div class="flex items-center justify-center">
          <div class="mt-3 text-center">
            <h3
              class="text-4xl leading-6 font-bold"
              :class="theme === 'light' ? 'text-gray-900' : 'text-gray-100'"
            >
              {{ header }}
            </h3>
            <div class="my-8">
              <p
                class="text-base"
                :class="theme === 'light' ? 'text-gray-500' : 'text-gray-100'"
              >
                {{ text }}
              </p>
            </div>
          </div>
        </div>

      </Modal>
    </teleport>
    
    <teleport to="#modals" v-if="showModalTwo">
      <Modal :theme=theme @close="toggleModalTwo">
        <!-- unnamed slot -->
        <div class="flex items-center justify-center">
          <div class="mt-3 text-center">
            <h3
              class="text-4xl leading-6 font-bold"
              :class="theme === 'light' ? 'text-gray-900' : 'text-gray-100'"
            >
              Modal 2
            </h3>
            <div class="my-8">
              <p class="text-base"
                :class="theme === 'light' ? 'text-gray-500' : 'text-gray-100'"
              >
                Well, this is just the second modal.
              </p>
            </div>
          </div>
        </div>
      </Modal>
    </teleport>

    <div class="pt-8">
      <button class="mx-2 rounded-md bg-purple-700 hover:bg-purple-600 transition duration-200 text-white p-4 text-xl" @click="toggleModal">First</button>
      <button class="mx-2 rounded-md bg-purple-700 hover:bg-purple-600 transition duration-200 text-white p-4 text-xl" @click="toggleModalTwo">Second</button>
    </div>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  components: { Modal },
  name: 'App',
  data() {
    return {
      title: "Vue Modal.",
      header: "Chance to Save!",
      text: "With very purchase.",
      theme: "dark",
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    // handleClick() {
    //   console.log(this.$refs.name.value)
    //   this.$refs.name.classList.toggle('active')
    // }
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  },
}
</script>

<style lang="scss">
  #app {
    background-color: $form_bg;
  }
</style>
