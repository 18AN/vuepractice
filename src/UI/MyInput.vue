<template>
  <input 
    class="input" 
    type="text"
    :value="modelValue"
    @input="updateInput"
    >
</template>

<script>
export default {
  props: {
    modelValue: [ String, Number ]
  },

  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>
    
<style>
    .input{
        width: 100%;
        border: 0.1rem solid darkseagreen;
        padding: 1rem;
        margin-top: 1rem;
    }
</style>