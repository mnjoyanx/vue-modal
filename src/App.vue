<template>
  <div>
    <v-modal :title="title" />
  </div>
</template>

<script>
import VModal from './components/V-Modal.vue'

export default {
  name: 'App',
  components: {
    VModal
  },
  data() {
    return {
      title: 'some title'
    }
  }
}
</script>

<style>
</style>
