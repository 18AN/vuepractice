<template>
  <div>
    <button @:click="addLike">Like</button>
    <button @:click="addDisLike">Dislike</button>
    <div>Total likes: {{likes}}</div>
    <div>Total dislikes: {{dislikes}}</div>
  </div>
</template>

<script>
export default {
    data(){
        return {
            likes:0,
            dislikes:0,
        }
    },
    methods: {
        addLike(){
            this.likes +=1;
        },
        addDisLike(){
            this.dislikes +=1;
        }
    }
}
</script>

<style>

</style>