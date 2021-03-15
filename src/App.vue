<template>
  <div class="wrapper">
    <div class="wrapper--content">

      <section>
        <div class="container">
          <button v-if="!isOpen" @click="isOpen = !isOpen" class="btn btn-lg btn-primary">open</button>
          <v-modal @closeModal="closeModal" :title="title" v-if="isOpen">
          </v-modal>        
        </div>
      </section>
      
    </div>
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
      title: 'some title',
      isOpen: false
    }
  },
  methods: {
    closeModal() {
      this.isOpen = false
    }
  }
}
</script>

<style>
</style>
