<template>
    <div class="post" v-for="post in posts">
        <div><strong>Title:</strong>{{post.title}}</div>
        <div><strong>Description:</strong>{{post.body}}</div>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
    .post{
        padding: 1rem;
        border: 0.2rem solid darkseagreen;
        margin-top: 1rem;
    }
</style>