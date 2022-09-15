<template>
  <div class="app">
    <post-form/>
    <post-list :posts="posts"/>
  </div>
</template>

<script>
import PostForm from '@/components/PostForm.vue'
import PostList from '@/components/PostList.vue'
export default {
    components: {
        PostForm, PostList
    },
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
            const newPost = {
                id: Date.now(),
                title: this.title,
                body: this.body,
            }
            this.posts.push(newPost)
            this.title = ''
            this.body = ''
        },
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
</style>