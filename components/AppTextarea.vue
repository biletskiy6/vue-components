<template>
  <div class="app-input">
    <textarea
      :id="name"
      :name="name"
      :value="value"
      v-bind="$attrs"
      :rows="rows"
      class="v-input v-text-field v-input theme--light v-text-field--is-booted"
      @input="$emit('input', $event.target.value)"
    />
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
    value: {
      required: false,
      type: String,
      default: '',
    },
  },
  computed: {
    rows() {
      return Math.max(5, this.value.split('\n').length)
    },
  },
}
</script>
