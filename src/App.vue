<template>
  <h1>{{ title }}</h1>
  <br />
  <input type="text" ref="name" />
  <button @click="handleClick">Click me</button>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal
      :header="header"
      text="Modal Content"
      theme="sale"
      @close="toggleModal"
    >
      <h2>This belongs to the slot</h2>
      <template v-slot:links>
        <a href="#">Sign up</a>
        <a href="#"> Sign in</a>
      </template>
    </Modal>
  </div>
  <button @click.alt="toggleModal">Open Modal -(alt)</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Sign up here",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      this.$refs.name.focus();
      this.$refs.name.classList.toggle("hello");
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
}
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
