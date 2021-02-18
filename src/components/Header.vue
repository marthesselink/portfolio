<template>
  <div class="header">
    <div class="row" v-if="page.title">
      <h1 class='col-md-12'>{{ page.title.rendered }}</h1>

      <div class="cta-block col-sm-12 col-lg-6 align-top">
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

      <div class="imageHeader col-sm-12 col-lg-6 d-flex flex-wrap align-items-center">
        <img
        v-if="acfData"
        class="ml-auto"
        :src="acfData.headerImage"
        :srcset="acfData.headerImage + ' 1x,' +
          acfData.headerImage2x + ' 2x'"/>
      </div>
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
    margin-bottom: 2rem;
  }

  .subtitle {
    font-weight: bold;
  }

  p {
    font-size: 25px;
  }

  .imageHeader {
    // position: relative;

    img {
      max-width: 100%;
    }
  }

  .socials {
    .btn {
      margin: 0 1rem 1rem 0;
      min-width: 80px;
    }
  }
</style>
