<template>
  <div class="github" id="github">
    <h2>Open Source</h2>

    <div v-if="repos" class="row">
      <div v-for="repo in repos" :key="repo.id" class="repo col-sm-12 col-md-6">
          <a :href="repo.html_url" target="_blank">
            <div class="card h-100">
              <h3 class="repo-title">{{ repo.name }}
                <svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" fill="currentColor" class="bi bi-link-45deg" viewBox="0 0 16 16">
                  <path d="M4.715 6.542L3.343 7.914a3 3 0 1 0 4.243 4.243l1.828-1.829A3 3 0 0 0 8.586 5.5L8 6.086a1.001 1.001 0 0 0-.154.199 2 2 0 0 1 .861 3.337L6.88 11.45a2 2 0 1 1-2.83-2.83l.793-.792a4.018 4.018 0 0 1-.128-1.287z"/>
                  <path d="M6.586 4.672A3 3 0 0 0 7.414 9.5l.775-.776a2 2 0 0 1-.896-3.346L9.12 3.55a2 2 0 0 1 2.83 2.83l-.793.792c.112.42.155.855.128 1.287l1.372-1.372a3 3 0 0 0-4.243-4.243L6.586 4.672z"/>
                </svg>
              </h3>
              <p class="h-100">{{ repo.description }}</p>
              <p>
                <b>{{ repo.language }}</b>
              </p>
            </div>
          </a>
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
  .repo {
    margin-bottom: 2rem;

    a {
      color: black;
      text-decoration: none;
    }

    .card {
      padding: 2rem;
      transition: all .2s ease-out;

      &:hover {
        background-color: #F5F5F5;

        h3 {
          text-decoration: underline;
        }
      }
    }
  }
</style>