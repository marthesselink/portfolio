<template>
  <div class="header col-xs-12 p-2 p-md-3 text-center">
    <div class="align-middle">
      <h1 class="display-3">{{ page.title.rendered }}</h1>
      <p class="lead" v-html="page.content.rendered"></p>

      <!-- <img
        class="headerimage ml-auto"
        :src="$static.pageBy.acfheader.headerimage.mediaItemUrl"
        :srcset="$static.pageBy.acfheader.headerimage.mediaItemUrl + ' 1x,' +
          $static.pageBy.acfheader.headerimage2x.mediaItemUrl + ' 2x'"/> -->

        <p>This website is built with Vue.js with a Headless WP installation as backend. Interested in a site? Contact me!</p>

        <!-- <div class="socials">
          <a class="btn btn-outline-secondary" :href="$static.pageBy.acfheader.linkedin.url">Linkedin</a>
          <a class="btn btn-outline-secondary" :href="$static.pageBy.acfheader.github.url">Github</a>
          <a class="btn btn-outline-secondary" :href="'mailto:' + $static.pageBy.acfheader.mail">Mail</a>
        </div> -->

        <a href="#projects" class="btn viewproject btn-outline-primary" id="#link">Recent Projects</a>
    </div>
  </div>
</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Header',
    data() {
      return {
        pageUrl: "http://wp.marthesselink.nl/wp-json/wp/v2/pages?slug=home",
        page: []
      };
    },
    methods : {
      getPageData() {
        axios
          .get(this.pageUrl)
          .then(response => {
            this.page = response.data[0];
            console.log('Page data retrieved!');
            console.log(this.page);
          })
          .catch(error => {
            console.log(error);
          });
      }
    },
    mounted() {
      this.getPageData();
    }
  };
</script>

<style scoped>
  h3 {
    margin: 40px 0 0;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: inline-block;
    margin: 0 10px;
  }
</style>
