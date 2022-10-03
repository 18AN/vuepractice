<template>
  <div class="dialog" v-if="show" @click="hideDialog">
    <div @click.stop class="dialog-content">
        <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
    props: {
        show: {
            type: Boolean,
            default: false,
        }
    },

    methods: {
        hideDialog() {
            this.$emit('update:show', false)
        }
    }
}
</script>

<style>
    .dialog {
        position: fixed;
        display: flex;
        left: 0;
        top: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, 0.5);
    }

    .dialog-content {
        padding: 1rem;
        margin: auto;
        background-color: white;
        border-radius: 1rem;
        min-width: 20rem;
    }
</style>