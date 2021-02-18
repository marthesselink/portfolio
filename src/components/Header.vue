<template>
  <div class="header">
    <div class="row" v-if="page.title">
      <h1 class='col-md-12'>{{ page.title.rendered }}</h1>

      <div class="cta-block col-md-6 align-top">
        <p class="subtitle" v-html="acfData.subtitle"></p>
        <p
          v-if="page.content"
          v-html="page.content.rendered">
        </p>

        <div v-if="acfData.linkedin" class="socials">
          <a class="btn btn-outline-secondary" :href="acfData.linkedin.url">Linkedin</a>
          <a class="btn btn-outline-secondary" :href="acfData.github.url">Github</a>
          <a class="btn btn-outline-secondary" :href="'mailto:' + acfData.mail">Mail</a>
        </div>
      </div>

      <div class="imageHeader col-md-6">
        <img
        v-if="acfData"
        class="ml-auto"
        :src="acfData.headerImage"
        :srcset="acfData.headerImage + ' 1x,' +
          acfData.headerImage2x + ' 2x'"/>
      </div>

      <!-- <div class="recent-work col-sm-12">
        <a href="#projects" class="btn viewproject btn-outline-primary" id="#link">Recent Projects</a>
      </div> -->
    </div>
  </div>

</template>

<script>
  import axios from 'axios';

  export default {
    name: 'Header',
    data() {
      return {
        pageUrl: "https://wp.marthesselink.nl/wp-json/wp/v2/pages?slug=home",
        page: [],
        acfUrl: "https://wp.marthesselink.nl/wp-json/acf/v3/pages/12",
        acfData: []
      };
    },
    methods : {
      getPageData() {
        axios
          .get(this.pageUrl)
          .then(response => {
            this.page = response.data[0];
            console.log('Page data retrieved!');
          })
          .catch(error => {
            console.log(error);
          });
      },
      getACFData() {
        axios
          .get(this.acfUrl)
          .then(response => {
            this.acfData = response.data.acf;
            console.log('ACF data retrieved!');
          })
          .catch(error => {
            console.log(error);
          });
      }
    },
    mounted() {
      this.getPageData();
      this.getACFData();
    }
  };
</script>

<style lang="scss" scoped>
  .header {
    max-width: 1140px;
    margin: 0 auto;
    width: 100%;
    padding: 40px;
  }

  .subtitle {
    font-weight: bold;
  }

  .imageHeader {
    position: relative;

    img {
      max-width: 800px;
      vertical-align: middle;
      width: 100%;
      position: absolute;
      top: 0;
      bottom: 0;
      margin: auto;
    }
  }

  .socials {
    .btn {
      margin: 0 1rem 1rem 0;
      min-width: 100px;
    }
  }

  .viewproject {
    width: 90%;
  }
</style>
