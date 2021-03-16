<template>
  <div class="wrapper">
    <div class="wrapper--content">

      <section>
        <div class="container">

            <button v-if="!isOpen" @click="isOpen = !isOpen" class="btn btn-lg btn-primary">open</button>          

            <v-modal @closeModal="closeModal" :title="title" v-show="isOpen">
              <div slot="content">
                this is modal content
              </div>
              <div slot="footer">
                <button class="btn btn-danger">close modal</button>
              </div>
            </v-modal>
         
            
                  
        </div>
      </section>

      <!-- <example-component /> -->
      
    </div>
  </div>
 
</template>

<script>
// import ExampleComponent from './components/ExampleComponent.vue'
import VModal from './components/V-Modal.vue'

export default {
  name: 'App',
  components: {
    VModal,
    // ExampleComponent
  },
  data() {
    return {
      title: 'some title',
      isOpen: false,
      isVisble: true
    }
  },
  methods: {
    closeModal() {
      this.isOpen = false
    }
  }
}
</script>

<style lang="scss">

</style>
