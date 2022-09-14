<template>
  <div class="app">
    <form>
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
        <button class="button" @click="createPost">Create</button>
    </form>
    <div class="post" v-for="post in posts">
        <div><strong>Title:</strong>{{post.title}}</div>
        <div><strong>Description:</strong>{{post.body}}</div>
    </div>
  </div>
</template>

<script>
export default {
    data(){
        return{
            posts: [
                {id: 1, title: 'Javascript', body: 'Description'},
                {id: 2, title: 'Javascript 2', body: 'Description 2'},
                {id: 3, title: 'Javascript 3', body: 'Description 3'},
            ],
            title: "",
            body: "" 
        }  
    },
    methods: {
        createPost(){

        },
        inputTitle(event){
            this.title = event.target.value;
        }
    }
}
</script>

<style >
    *{
        margin: 0px;
        padding: 0px;
        box-sizing: border-box;
    }

    .app{
        padding: 2rem;
    }

    .post{
        padding: 1rem;
        border: 0.2rem solid darkseagreen;
        margin-top: 1rem;
    }

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