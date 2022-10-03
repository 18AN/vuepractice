<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <my-button @click="showDialog">Создать пост</my-button>
    <my-form-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-form-dialog>
    <post-list :posts="posts" @deletePost="deletePost" />
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyFormDialog from "./UI/MyFormDialog.vue";
import MyButton from "./UI/MyButton.vue";
export default {
  components: {
    PostForm,
    PostList,
    MyFormDialog,
    MyButton,
  },

  data() {
    return {
      posts: [
        { id: 1, title: "Javascript", body: "Description" },
        { id: 2, title: "Javascript 2", body: "Description 2" },
        { id: 3, title: "Javascript 3", body: "Description 3" },
      ],
      dialogVisible: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },

    deletePost(post) {
      this.posts = this.posts.filter((item) => item.id !== post.id);
    },

    showDialog() {
      this.dialogVisible = true;
    },
  },
};
</script>

<style>
* {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
}

.app {
  padding: 2rem;
}
</style>