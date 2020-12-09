<template>
  <div class="recentprojects container" id="projects">
    <h2 class="text-center display-4">Recent Projects</h2>

    <div v-if="posts" class="row">
      <div v-for="post in posts" :key="post.id" class="project col-sm-12 col-md-6">

        <a :href="post.acf.link" target="_blank">
          <div class="card">
            <h3 class="project-title">{{ post.title.rendered }}</h3>
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
        postsUrl: "http://wp.marthesselink.nl/wp-json/wp/v2/posts",
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
            console.log(this.posts);
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
    min-height: 100vh;
    margin-bottom: 2rem;

    .screenshot {
      width: 100%;
      max-height: 270px;
      margin-bottom: 20px;
    }
  }

  h2 {
    margin-bottom: 1rem;
  }

  .project {
    padding: 10px;
  }

  h3 {
    font-size: 1.5rem;

    @media(min-width: 992px) {
      font-size: 2rem;
    }
  }

  a {
    color: black;

    &:hover {
      text-decoration: none;
      color: black;
    }
  }

  .card {
    padding: 20px;
    max-height: 100%;
  }
</style>