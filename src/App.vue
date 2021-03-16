<template>
  <div class="wrapper">
    <div class="wrapper--content">

      <section>
        <div class="container">

            <button v-if="!isOpen" @click="isOpen = !isOpen" class="btn btn-lg btn-primary">open</button>          

            <!-- first modal -->
            <v-modal @closeModal="closeModal" :title="title" v-show="isOpen">
              <div slot="content">
                this is modal content
              </div>
              <div slot="footer">
                <button class="btn btn-danger">close modal</button>
              </div>
            </v-modal>
            <!-- first modal -->
         
            <!-- second modal -->

            <button v-if="!secondModal.show" @click="secondModal.show = !secondModal.show" class="btn ml-3 d-block btn-lg btn-primary">open second modal</button>
            <v-modal @closeModal="closeSecondModal" :title="secondModal.title" v-show="secondModal.show">
              <form action="" slot="content" @submit.prevent="submitForm">

                <div class="form-group" :class="{ 'form-group--error': $v.secondModal.name.$error }">
                  <label for="name">Name</label>
                  <input type="text" v-model.trim="$v.secondModal.name.$model" class="form-control" id="name" aria-describedby="nameHelp" placeholder="Enter Name">
                </div>
                <div class="error" v-if="!$v.secondModal.name.required && $v.secondModal.name.$dirty">Field is required</div>

                <div class="form-group" :class="{ 'form-group--error': $v.secondModal.email.$error }">
                  <label for="exampleInputEmail1">Email address</label>
                  <input type="email" v-model.trim="$v.secondModal.email.$model" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
                </div>
                <div class="error" v-if="!$v.secondModal.email.required && $v.secondModal.email.$dirty">Field is required</div>

                
                <div slot="footer"> 
                  <button class="btn btn-danger">close modal</button>
                </div>
              </form>

             
            </v-modal>
            <!-- second modal -->
            {{ $v }}

            
                  
        </div>
      </section>

      <!-- <example-component /> -->
      
    </div>
  </div>
 
</template>

<script>

import { required, minLength } from 'vuelidate/lib/validators'

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
      secondModal: {
        show: false,
        name: '',
        email: '',
        title: 'Second Modal Title'
      }
    }
  },
  validations: {
    secondModal: {
      name: {
          required,
         minLength: minLength(6)
        },
        email: {
          required
        }
    }
       
    },
  methods: {
    submitForm() {
      this.$v.$touch()
        console.log(this.secondModal)
    },
    closeModal() {
      this.isOpen = false
    },
    closeSecondModal() {
      this.secondModal.show = false
    }
  }
}
</script>

<style lang="scss">
  .error {
    color: red;
  }
</style>
