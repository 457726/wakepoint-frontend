<template>
    <div>
        <h4 class="w3-center w3-padding-64">
            <span class="post"> {{ post.title }} </span>
        </h4>
            <br>
            {{ post.description }}
            <br>
            <b-button variant="danger" class="btn" type="submit" @click="deletePost(); $router.push({ path:`/beers`})">Delete</b-button>
            <b-button variant="warning"><router-link :to="'/edit/' + `${post.id}`">Edit</router-link></b-button>

    </div>
</template>

<script>
import axios from "axios";
import VueAxios from "vue-axios";
import Vue from "vue";
Vue.use(VueAxios, axios);
export default {

  name: "PostView",
  components: {},
  data() {
      return {
      post: null,
      title : null,
      postid : null,
    };
  },
  mounted() {
    this.postid = this.$route.params.id;
    axios
        .get('https://localhost:44375/api/ForumPosts/' + this.postid).then((response) => {
      this.post = response.data;
      console.warn(this.post);
    })
  },
  methods:
  {
  deletePost(){
    axios({
        method: 'delete',
        url: 'https://localhost:44375/api/ForumPosts/' + this.postid    
    })
  }
}
};
</script>