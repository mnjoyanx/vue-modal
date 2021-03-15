<template>
    <div>
        this is example component
        <v-modal>
            <input slot="footer">
        </v-modal>
    </div>
</template>

<script>
import VModal from './V-Modal.vue'
    export default {
  components: { VModal },
        name: 'example-component'
    }
</script>

<style lang="scss" scoped>

</style>