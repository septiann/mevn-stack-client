<template>
  <div class="posts">
    <h1>Add Post</h1>
    <div>
      <router-link v-bind:to="{ name: 'Posts' }" class="">Back</router-link>
    </div>
    <div class="form">
      <div>
        <input type="text" name="title" placeholder="Title" v-model="title" />
      </div>
      <div>
        <textarea
          name="description"
          id="description"
          cols="15"
          rows="15"
          placeholder="Description"
          v-model="description"
        ></textarea>
      </div>
      <div>
        <button class="app_post_btn" @click="addPost">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
import PostsService from "@/services/PostsService";
export default {
  name: "NewPost",
  data() {
    return {
      title: "",
      description: ""
    };
  },
  methods: {
    async addPost() {
      await PostsService.addPost({
        title: this.title,
        description: this.description
      });
      this.$router.push({ name: "Posts" });
    }
  }
};
</script>

<style type="text/css">
.form input,
.form textarea {
  width: 500px;
  padding: 10px;
  border: 1px solid #e0dede;
  outline: none;
  font-size: 12px;
}
.form div {
  margin: 20px;
}
.app_post_btn {
  background: #4d7ef7;
  color: #fff;
  padding: 10px 80px;
  text-transform: uppercase;
  font-size: 12px;
  font-weight: bold;
  width: 520px;
  border: none;
  cursor: pointer;
}
</style>
