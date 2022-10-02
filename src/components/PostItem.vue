<template>
    <div class="post">
        <div>
            <div><strong>Title:</strong>{{post.title}}</div>
            <div><strong>Description:</strong>{{post.body}}</div>
        </div>
        <div class="buttons">
            <my-button
                @click="$emit('deletePost', post)"
            >
                Delete
            </my-button>
        </div>
    </div>
    
</template>

<script>
import MyButton from '@/UI/MyButton.vue'
export default {
    components: { MyButton },
    props: {
        post: {
            type: Object,
            required: true,
        }
    },
}
</script>

<style scoped>
    .post{
        padding: 1rem;
        border: 0.2rem solid darkseagreen;
        margin-top: 1rem;
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
</style>