<template>
    <div>
        <div>
            <h1>New post</h1>
            <hr /><br />
        </div>
        <div>

            <div class="create">
                <h4>Post:</h4>
                <b-form-textarea class="form"
                                 v-model="form.title"
                                 placeholder="Fill in the name of your post here">
                </b-form-textarea>
                <b-form-textarea class="form"
                                 v-model="form.description"
                                 placeholder="Fill in the description of your post here"
                                 rows="10"
                                 max-rows="5">
                </b-form-textarea>
                <b-form-textarea class="form"
                                 v-model="form.category"
                                 placeholder="Choose the category here"
                                 rows="3"
                                 max-rows="5">
                </b-form-textarea>
            </div>
            <b-button variant="primary" class="btn" type="submit" @click="onSubmit"><a @click="$router.go(-1)" class="nav">Submit</a></b-button>
        </div>
    </div>
</template>

<script>
  import axios from 'axios'
  import VueAxios from 'vue-axios'
  import Vue from 'vue'
  import VueRouter from 'vue-router'
  Vue.use(VueRouter)
  Vue.use(VueAxios, axios, VueRouter)
  export default {
      name: 'CreateView',
      components: {
      },
      data() {
          return {
              form: {
                  title: '',
                  description: '',
                  category: ''
              }
          }
      },
      methods: {
          onSubmit(event) {
              event.preventDefault()
              console.warn(this.form)
              axios({
                  method: 'post',
                  url: 'https://localhost:44375/api/ForumPosts',
                  data: {
                      "title": this.form.title,
                      "description": this.form.description,
                      "category": this.form.category
                  }
              })
          }
      }
  }
</script>

<style scoped>
    .create {
        margin-left: 50px;
        margin-bottom: 25px;
        margin-right: 50px;
    }

    .form {
        margin-top: 25px;
        margin-bottom: 25px;
    }

    .btn {
        margin-left: 10px;
    }

    .nav {
        color: white;
    }
</style>