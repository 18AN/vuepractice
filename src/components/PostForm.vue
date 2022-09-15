<template>
    <form  @submit.prevent>
        <h4>Create Post</h4>
        <input 
            v-bind:value="title" 
            @input="title = $event.target.value" 
            class="input" 
            type="text" 
            name="title" 
            placeholder="Title">
        <input 
            v-bind:value="body" 
            @input="body = $event.target.value"
            class="input" 
            type="text" 
            name="description" 
            placeholder="Description">
        <button class="button">Create</button>
    </form>
</template>

<script>
export default {

}
</script>

<style scoped>
    form{
        display: flex;
        flex-direction: column;
    }

    .input{
        width: 100%;
        border: 0.1rem solid darkseagreen;
        padding: 1rem;
        margin-top: 1rem;
    }

    .button{
        align-self: flex-end;
        margin-top: 1rem;
        padding: 0.7rem;
        background: none;
        color: darkseagreen;
        border: 0.1rem solid darkseagreen;
    }
</style>