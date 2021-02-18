<template>
  <div class="recentprojects" id="projects">
    <h2>Recent Projects</h2>

    <div v-if="posts" class="row">
      <div v-for="post in posts" :key="post.id" class="project col-sm-12 col-lg-6">
        <a :href="post.acf.link" target="_blank">
          <div class="card h-100">
            <h3>{{ post.title.rendered }}</h3>
            <img
                v-if="post.acf"
                :alt="post.acf.title"
                :src="post.acf.screenshot.url"
                class="screenshot"/>
            <button class="btn btn-outline-primary" id="#link">View Project</button>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'RecentProjects',
    data() {
      return {
        postsUrl: "https://wp.marthesselink.nl/wp-json/wp/v2/posts",
        posts: []
      };
    },
    methods : {
      getPostData() {
        axios
          .get(this.postsUrl)
          .then(response => {
            this.posts = response.data;
            console.log('Post data retrieved!');
          })
          .catch(error => {
            console.log(error);
          });
      }
    },
    mounted() {
      this.getPostData();
    }
  }
</script>

<style lang="scss" scoped>
  .recentprojects {
    a {
      color: black;

      &:hover {
        text-decoration: none;
        color: black;
      }
    }

    .project {
      margin-bottom: 2rem;

      .card {
        padding: 2rem;
        transition: all .2s ease-out;

        .screenshot {
          width: 100%;
          margin-bottom: 20px;
        }

        &:hover {
          background-color: #F5F5F5;

          h3 {
            text-decoration: underline;
          }
        }
      }
    }
  }
</style>