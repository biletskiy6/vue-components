<template>
  <AppModal name="signin">
    <template slot="body">
      <h1>Sign In</h1>
      <a href="#" @click="closeModal">Close my modal</a>
    </template>
  </AppModal>
</template>

<script>
import AppModal from '@/components/AppModal'
export default {
  name: 'AppSignInModal',
  components: {
    AppModal,
  },
  methods: {
    closeModal() {
      this.$modal.hide('signin')
    },
  },
}
</script>
