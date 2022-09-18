<template>
    <form  @submit.prevent>
        <h4>Create Post</h4>
        <input 
            v-model="post.title" 
            class="input" 
            type="text" 
            name="title" 
            placeholder="Title">
        <input 
            v-model="post.body"
            class="input" 
            type="text" 
            name="description" 
            placeholder="Description">
        <button class="button">Create</button>
    </form>
</template>

<script>
export default {
    data(){
        return {
            post: {
                title: '',
                body: '',
            }
        }
    }
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