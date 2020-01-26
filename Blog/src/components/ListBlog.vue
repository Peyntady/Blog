<template>
  <ul>
    <Post
            v-bind:REG="REG_FLAG"
            v-on:edit-post="editPost"
            v-for="post of listPost.posts"
            v-bind:key="post.id"
            v-bind:post="post"
    />
  </ul>
</template>

<script>
  import Post from "@/components/Post";
  export default {
    data(){
      return{
        listPost: require('@/data-post')
      }
    },
    name: "ListBlog",
    props: ['REG_FLAG'],
    components: {
      Post
    },
    methods: {
      editPost(id){
        this.listPost.idNow = id;
        this.$emit('edit-post');
      }
    },
  }
</script>

<style scoped>
  ul {
    list-style-type: none;
    margin-top: 20px;
    padding: 0;
  }
</style>