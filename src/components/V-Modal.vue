<template>
    <transition name="modal">
        <div class="modal--wrapper" @click="$emit('closeModal')">
            <div class="modal--content" @click.stop="">
    
                 <!-- Modal Header -->
                <div class="modal--header">
                    <span class="modal--title"> {{ title }} </span>
                    <span class="modal--close" @click="$emit('closeModal')">&#x2715;</span>
                </div>
                <!-- Modal Header -->
    
                <!-- Modal Content -->
                <div class="modal--content">
                    <slot name="content" />
                </div>
    
                <div class="footer">
                    <slot name="footer" />
                   
                </div>
                <!-- Modal Content -->
    
            </div>
        </div>
    </transition>
       
   
</template>

<script>
    export default {
        name: 'v-modal',
        props: {
            title: {
                type: String,
                default: 'V-Modal'
            }
        },
        mounted() {
            document.body.addEventListener('keyup', e => {
                if(e.code === 'Escape')  {
                    this.$emit('closeModal')
                }
            })
        }
    }
</script>

<style lang="scss" scoped>
    
    .modal-enter, .modal-leave-active {
        opacity: 0;
        
    }

    .modal-enter .modal--content,
    .modal-leave-active .modal--content {
        transform: scale(1.2);
    }

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

    .modal--header {
        display: flex;
        align-self: center;
        justify-content: space-between;
        padding-bottom: 20px;
        span {
            font-size: 24px
        }

        .modal--close {
            cursor: pointer
        }
        .modal--content {   
            text-align: center;
        }
    }
</style>