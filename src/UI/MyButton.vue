<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script>
export default {

}
</script>

<style scoped>
    .button{
        min-width: 8rem;
        padding: 0.7rem;
        background: none;
        color: darkseagreen;
        border: 0.1rem solid darkseagreen;
    }
</style>