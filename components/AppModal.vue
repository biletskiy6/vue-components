<template>
  <div v-if="visible" class="app-modal" @click="$modal.hide(name)">
    <div class="app-modal-inner" @click.stop>
      <slot name="body" :params="params" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppModal',
  props: {
    name: {
      required: true,
      type: String,
    },
  },
  data() {
    return {
      params: {},
      visible: false,
    }
  },
  beforeMount() {
    this.$modal.$event.$on('show', (modal, params) => {
      this.params = params
      return this.name === modal ? (this.visible = true) : null
    })
    this.$modal.$event.$on('hide', (modal) => {
      return this.name === modal ? (this.visible = false) : null
    })
  },
  mounted() {
    document.addEventListener('keydown', (e) => {
      if (this.visible && e.which === 27) {
        this.visible = false
      }
    })
  },
}
</script>

<style lang="scss">
.app-modal {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background: rgba(#000016, 0.4);
  z-index: 101;
  &-inner {
    background: #fff;
    border-radius: 12px;
    width: 100%;
    max-width: 600px;
    padding: 40px;
    //background: red;
  }
}
</style>
