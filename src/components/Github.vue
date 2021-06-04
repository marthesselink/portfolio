<template>
  <div class="github container" id="github">
    <div class="text">
      <p class="subtitle">Open Source</p>
      <hr>
      <h2>Featured Open Source</h2>

      <p>Take a look at the projects I've made on my Github.</p>
    </div>

    <div v-if="repos" class="row row-cols-1 row-cols-lg-2">
      <div v-for="repo in repos" :key="repo.id">
        <div class="repo">
          <a :href="repo.html_url" target="_blank">
            <div class="card h-100">
              <h3 class="repo-title">{{ repo.name }}
                <svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-link-45deg" viewBox="0 0 16 16">
                  <path d="M4.715 6.542L3.343 7.914a3 3 0 1 0 4.243 4.243l1.828-1.829A3 3 0 0 0 8.586 5.5L8 6.086a1.001 1.001 0 0 0-.154.199 2 2 0 0 1 .861 3.337L6.88 11.45a2 2 0 1 1-2.83-2.83l.793-.792a4.018 4.018 0 0 1-.128-1.287z"/>
                  <path d="M6.586 4.672A3 3 0 0 0 7.414 9.5l.775-.776a2 2 0 0 1-.896-3.346L9.12 3.55a2 2 0 0 1 2.83 2.83l-.793.792c.112.42.155.855.128 1.287l1.372-1.372a3 3 0 0 0-4.243-4.243L6.586 4.672z"/>
                </svg>
              </h3>
              <p class="description">{{ repo.description }}</p>
              <p>
                <b class="language">{{ repo.language }}</b>
              </p>
            </div>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Github',
    data() {
      return {
        reposUrl: "https://api.github.com/users/marthesselink/repos",
        repos: []
      };
    },
    methods : {
      getGithubData() {
        axios
          .get(this.reposUrl)
          .then(response => {
            this.repos = response.data;
            console.log('Github data retrieved!');
          })
          .catch(error => {
            console.log(error);
          });
      }
    },
    mounted() {
      this.getGithubData();
    }
  }
</script>

<style lang="scss" scoped>
  .github {
    margin-bottom: 80px;
  }

  .repo {
    margin: 10px 0;
    box-shadow: 0px 28px 14px -16px $shadow;

    @media (min-width: 992px) {
      margin: 20px 20px;
    }

    a {
      text-decoration: none;
    }

    .card {
      padding: 25px;
      transition: all .2s ease-out;
      background-color: $highlight;

      .repo-title {
        color: $white;
        font-size: 30px;
      }

      .description {
        color: $grey;

      }

      .language {
        color: $orange;
      }

      &:hover {
        .repo-title {
          text-decoration: underline;
        }
      }
    }
  }
</style>