<template>
  <nuxt-link
    class="v-btn"
    :class="[themes[theme], sizes[size]]"
    :to="to"
    @click.native="handleClick"
    ><slot
  /></nuxt-link>
</template>
<script>
export default {
  props: {
    theme: {
      required: false,
      type: String,
      default: 'primary',
    },
    size: {
      required: false,
      type: String,
      default: 'v-size--default',
    },
    to: {
      required: false,
      type: Object,
      default: () => ({
        name: 'index',
      }),
    },
  },
  data: () => ({
    themes: {
      primary: 'primary',
      error: 'error',
    },
    sizes: {
      default: 'v-size--default',
      large: 'v-size--large',
    },
  }),
  methods: {
    handleClick(e) {
      this.$emit('click', e)
    },
  },
}
</script>
