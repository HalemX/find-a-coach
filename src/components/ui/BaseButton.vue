<template>
  <button v-if="!link" :class="mode"><slot></slot></button>
  <router-link v-else :to="to" :class="mode"><slot></slot></router-link>
</template>

<script>
export default {
  props: {
    mode: {
      type: String,
      required: false,
      default: null,
    },
    link: {
      type: Boolean,
      required: false,
      default: false,
    },
    to: {
      type: String,
      required: false,
      default: '/',
    },
  },
};
</script>

<style scoped>
button,
a {
  text-decoration: none;
  padding: 0.75rem 1.5rem;
  font: inherit;
  background-color: #8d6e63;
  border: 1px solid #8d6e63;
  color: white;
  cursor: pointer;
  border-radius: 30px;
  margin-right: 0.5rem;
  display: inline-block;
  transition: 0.3s;
}

a:hover,
a:active,
button:hover,
button:active {
  background-color: #b1806e;
  border-color: #b1806e;
}

.flat {
  background-color: transparent;
  color: #b1806e;
  border: none;
}

.outline {
  background-color: transparent;
  border-color: #b1806e;
  color: #795548;
}

.flat:hover,
.flat:active,
.outline:hover,
.outline:active {
  background-color: #e6dad6;
}
</style>
