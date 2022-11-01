<template>
  <div class="app">
    <h1>Страница с постами</h1>
    <my-input
      class="search"
      placeholder="Поиск по заголовку"
      v-model="searchQuery"
    />
    <div class="app_btns">
      <my-button @click="showDialog">Создать пост</my-button>
      <my-select
        v-model="selectedSort"
        :options="sortOptions"
      />
    </div>
    <my-form-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </my-form-dialog>
    <post-list v-if="!isPostsLoading" :posts="searchedPosts" @deletePost="deletePost" />
    <div v-else>Posts loading...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyFormDialog from "@/UI/MyFormDialog.vue";
import MyButton from "@/UI/MyButton.vue";
import axios from "axios";
import MySelect from './UI/MySelect.vue';
import MyInput from "@/UI/MyInput.vue";
export default {
  components: {
    PostForm,
    PostList,
    MyFormDialog,
    MyButton,
    MySelect,
    MyInput,
  },

  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort: "",
      sortOptions: [
        {value: "title", name: "По названию"},
        {value: "body", name: "По описанию"},
      ],
      searchQuery: "",
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
  },
  computed: {
      sortedPosts() {
        return [...this.posts].sort((post1,post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
      },
      searchedPosts() {
        return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
      }
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

.search {
  margin-bottom: 25px ;
}

.app_btns {
  display: flex;
  justify-content: space-between;
}
</style>