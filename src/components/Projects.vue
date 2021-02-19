<template>
  <div class="projects" id="projects">
    <h2>Recent Projects</h2>

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

              <div class="row no-margin">
                <p v-if="post.acf.tag1">
                  <span class="badge bg-secondary tag1">
                    {{ post.acf.tag1 }}
                  </span>
                </p>
                <p v-if="post.acf.tag2">
                  <span class="badge bg-secondary">
                    {{ post.acf.tag2 }}
                  </span>
                </p>
                <p v-if="post.acf.tag3">
                  <span class="badge bg-secondary">
                    {{ post.acf.tag3 }}
                  </span>
                </p>
              </div>

              <!-- <button class="btn btn-outline-primary" id="#link">View Project</button> -->
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
    a {
      color: black;

      &:hover {
        text-decoration: none;
        color: black;

        h3 {
          text-decoration: underline;
        }
      }
    }

    .project {
      margin-bottom: 2rem;

      .screenshot {
        width: 100%;
        margin: 0 auto 20px;
      }

      .no-margin {
        margin: 0 auto 0;
      }

      .badge {
        color: white;
        padding: 5px;
        margin-left: 10px;
      }

      .tag1 {
        margin-left: 0;
      }
    }
  }
</style>