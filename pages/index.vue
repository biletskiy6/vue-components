<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <AppSignInModal></AppSignInModal>

      <a href="#" @click="handleClick">Open Modal</a>
    </v-col>
  </v-row>
</template>
<script>
import AppSignInModal from '@/components/modals/AppSignInModal'

export default {
  components: {
    AppSignInModal,
  },
  data() {
    return {
      form: {
        email: '',
        bio: '',
      },
    }
  },
  methods: {
    handleClick() {
      this.$modal.show('signin')
    },
  },
}
</script>
