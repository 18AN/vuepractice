<template>
    <form  @submit.prevent>
        <h4>Create Post</h4>
        <my-input 
            v-model="post.title" 
            name="title" 
            placeholder="Title">
        </my-input>
        <my-input 
            v-model="post.body"
            name="description" 
            placeholder="Description">
        </my-input>
        <my-button
            class="form__button"
            @click="createPost">
            Create
        </my-button>
    </form>
</template>

<script>
import MyButton from '@/UI/MyButton.vue'
import MyInput from '@/UI/MyInput.vue'
export default {
  components: { MyButton, MyInput },
    data(){
        return {
            post: {
                title: '',
                body: '',
            }
        }
    },
    methods: {
        createPost(){
            this.post.id = Date.now()
            this.$emit('create', this.post)
            this.post = {
                title: '',
                body: '',
            }
        },
    }
}
</script>

<style scoped>
    form{
        display: flex;
        flex-direction: column;
    }

    .form__button{
        margin-top: 1rem;
        align-self: flex-end;
    }

</style>