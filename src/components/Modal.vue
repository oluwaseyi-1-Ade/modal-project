<template>
  <div class="backdrop" @click.self="closeModal">
    <div class="modal" :class="{ sale: theme === 'sale' }">
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
      <slot></slot>
      <div class="actions">
        <slot name="links"></slot>
      </div>
      <div class="slot-two">
        <slot name="links-two"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["header", "text", "theme"],
  methods: {
    closeModal() {
      this.$emit("close");
    },
  },
};
</script>

<style>
.modal {
  width: 450px;
  padding: 20px;
  margin: 100px auto;
  background: white;
  border-radius: 10px;
}

.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
}

.modal h1,
.modal p {
  color: #333;
}

.modal .actions,
.slot-two {
  text-align: center;
  margin: 30px 0 10px 0;
  /* background: red; */
}

.modal .actions a,
.slot-two a {
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.sale {
  background: red;
  color: white;
}

.sale h1,
.sale p {
  color: white;
}

.sale .actions a {
  color: white;
}
</style>

// slots are like an alternative for props, but they are used when passing //
templates
