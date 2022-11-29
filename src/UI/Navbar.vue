<template>
    <div class="navbar">
        <div @click="$router.push('/')">App</div>
        <div class="navbar__btns">
            <my-button @click="$router.push('/posts')">Posts</my-button>
            <my-button @click="$router.push('/about')">About</my-button>
        </div>
    </div>
</template>

<script>
import MyButton from './MyButton.vue'
export default {
  components: { MyButton },

}
</script>

<style>
    .navbar {
        height: 50px;
        background-color: bisque;
        display: flex;
        align-items: center;
        padding: 0 15px;
    }

    .navbar__btns {
        margin-left: auto;
    }
</style>