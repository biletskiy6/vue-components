<template>
  <div class="app-input">
    <input
      :id="name"
      :name="name"
      :type="inputType"
      :value="value"
      v-bind="$attrs"
      class="v-input v-text-field v-input theme--light v-text-field--is-booted"
      @input="$emit('input', $event.target.value)"
    />
    <a
      v-if="type === 'password'"
      href="#"
      @click.prevent="togglePasswordVisibility"
      >Reveal Password</a
    >
  </div>
</template>

<script>
export default {
  name: 'AppInput',
  props: {
    name: {
      required: true,
      type: String,
    },
    type: {
      required: false,
      type: String,
      default: 'text',
    },
    value: {
      required: false,
      type: String,
      default: '',
    },
  },
  data: () => ({
    passwordRevealed: false,
  }),
  computed: {
    inputType() {
      return this.passwordRevealed ? 'text' : this.type
    },
  },
  methods: {
    togglePasswordVisibility() {
      this.passwordRevealed = !this.passwordRevealed
    },
  },
}
</script>
