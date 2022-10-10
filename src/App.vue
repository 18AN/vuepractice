<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <my-button @click="showDialog">Создать пост</my-button>
    <my-form-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-form-dialog>
    <post-list v-if="!isPostsLoading" :posts="posts" @deletePost="deletePost" />
    <div v-else>Posts loading...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyFormDialog from "./UI/MyFormDialog.vue";
import MyButton from "./UI/MyButton.vue";
import axios from "axios";
export default {
  components: {
    PostForm,
    PostList,
    MyFormDialog,
    MyButton,
  },

  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
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

    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        setTimeout(async () => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
          this.posts = response.data;
          this.isPostsLoading = false;
        }, 1000);        
      } catch(e) {
        alert('Error');
      }
    }
  },
  mounted() {
    this.fetchPosts();
  }
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