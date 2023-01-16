<template>
    <div class="home">
        <b-card-group style="margin: 80px;">
            <b-card v-for="post in postList"
                    :key="post.id"
                    :title="post.title"
                    img-top
                    tag="post"
                    style="max-width: 18rem; margin: 40px"
                    class="mb-2"
                    align="center">
                <b-button variant="warning" name="info"><router-link :to="'/post/' + `${post.id}`">More info</router-link></b-button>
            </b-card>
        </b-card-group>
    </div>
</template>

<script>
    import axios from "axios";
    import VueAxios from "vue-axios";
    import Vue from "vue";

    Vue.use(VueAxios, axios);

    export default {
        name: "HomeView",
        components: {},
        data() {
            return {
                postList: null,
            };
        },
        mounted() {
            axios.get("https://localhost:44375/api/ForumPosts/Posts").then((response) => {
                this.postList = response.data;
                console.warn(this.postList);
            });
        },

    }
</script>