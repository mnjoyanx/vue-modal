<template>
    <div class="modal--wrapper">
        <div class="modal--content">
            <div class="modal--header">
                <span class="modal--title"> {{ title }}} </span>
                <span class="modal--close"></span>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'v-modal',
        props: {
            title: {
                type: String,
                default: 'V-Modal'
            }
        }
    }
</script>

<style lang="scss" scoped>
    .modal--wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        transition: opacity .3s ease;
        right: 0;
        z-index: 999;
        background-color: rgba(0, 0, 0, .48);
    }

    .modal--content {
        position: realative;
        max-width: 600px;
        padding: 20px 18px;
        background-color: #fff;
          
    }
</style>