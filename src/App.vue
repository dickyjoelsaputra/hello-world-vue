<template>
  <div>
    <div>
      <h1>{{ name }}</h1>
    </div>
    <h1>{{ title }}</h1>
    <div v-if="showModal">
      <Modal :array="['shaun', 4]" :header="header" :text="text" theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">Sign Up Now</a>
          <a href="#">More Info</a>
        </template>
        <!-- <template>
        <p>template tanpa v-slot</p>
      </template> -->
        <h1>INI SLOT</h1>
      </Modal>
    </div>

    <teleport to=".modal" v-if="showModalTwo">
      <Modal @close="toggleModalTwo">
        <template v-slot:links>
          <a href="#">Sign Up Now</a>
          <a href="#">More Info</a>
        </template>
      </Modal>
    </teleport>

    <button @click="toggleModal">open modal</button>
    <button @click="toggleModalTwo">open modal two</button>
    <input type="text" ref="name">
    <button @click="handleClick">click me!</button>
  </div>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      name: "titid",
      title: "My First Vue App :)",
      header: "Sign Up For Free",
      text: "grab your ninja swag",
      array: ['shaun', 4],
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name.value)
      this.name = this.$refs.name.value
      this.$refs.name.classList.add('active')
      this.$refs.name.value = ''
      this.$refs.name.focus()
    },
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
