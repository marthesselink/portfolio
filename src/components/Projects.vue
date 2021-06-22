<template>
  <div class="projects container" id="projects">
    <div class="text">
      <p class="subtitle">Projects</p>
      <hr>
      <h2>My Recent Creations</h2>

      <p>Take a look at some of the projects I've made.</p>
    </div>

    <div v-if="posts" class="row">
      <div v-for="(post, index) in posts" :key="post.id" class="project col-lg-12 ">
        <a :href="post.acf.link" target="_blank">
          <div class="h-100 row">
            <div class="image col-md-6"
            :class="{'order-md-1':index%2 != 1}">
              <img
                v-if="post.acf"
                :alt="post.acf.title"
                :src="post.acf.screenshot.url"
                class="screenshot"/>
            </div>

            <div class="description col-md-6 justify-content-center align-self-center"
            :class="{'order-md-1':index%2 === 1}">
              <h3>{{ post.title.rendered }}</h3>
              <p
                v-if="post.content"
                v-html="post.content.rendered">
              </p>

              <div class="no-margin">
                <p v-if="post.acf.tag1">
                  <span class="badge">
                    {{ post.acf.tag1 }}
                  </span>
                </p>
                <p v-if="post.acf.tag2">
                  <span class="badge">
                    {{ post.acf.tag2 }}
                  </span>
                </p>
                <p v-if="post.acf.tag3">
                  <span class="badge">
                    {{ post.acf.tag3 }}
                  </span>
                </p>
              </div>
            </div>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Projects',
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
  .projects {
    margin-bottom: 80px;

    a {
      text-decoration: none;
    }
    .project {
      padding: 10px;
      margin: 10px;
      border-radius: 5px;
      transition: all .2s ease-out;

      @media (min-width: 768px) {
        margin: 20px 20px;
        padding: 40px;
      }

      &:hover {
        background-color: $highlight;
        cursor: pointer;
      }

      .description {
        p {
          color: $grey;
        }
      }

      .image {
        text-align: center;

        .screenshot {
          width: 80%;
          margin: 0 auto 20px;
        }
      }

      .no-margin {
        margin: 0 auto 0;
      }

      .badge {
        color: $orange;
        background-color: $orange-seethrough;
        padding: 7px 20px;
        margin-right: 15px;
        margin-bottom: 10px;
        border-radius: 40px;
        float: left;
      }
    }
  }
</style>