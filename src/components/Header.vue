<template>
  <div class="container-fluid">
    <div class="header">
      <div class="container">
        <div class="row" v-if="page.title">

          <div class="col-md-12 col-lg-7 col-sm-12 order-2 order-lg-1">
            <h6 v-html="acfData.toptitle"></h6>
            <h1>{{ acfData.firstname }} <span class="lastname">{{ acfData.lastname }}</span> <span class="dot">.</span></h1>
            <h2 class="header-subtitle" v-html="acfData.subtitle"></h2>
            <p
              v-if="page.content"
              v-html="page.content.rendered"
              class="content">
            </p>

            <div v-if="acfData.linkedin" class="socials">
              <a class="outline" :href="acfData.linkedin.url" target="_blank">Linkedin</a>
              <a class="outline" :href="acfData.github.url" target="_blank">Github</a>
              <a class="filled" href="#contact">Contact me</a>
            </div>
          </div>

          <div class="imageHeader col-md-12 col-lg-5 col-md-12 col-sm-12 order-1 order-lg-2">
            <img
            v-if="acfData"
            :src="acfData.headerImage"
            :srcset="acfData.headerImage + ' 1x,' +
              acfData.headerImage2x + ' 2x'"/>
          </div>

        </div>
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
  .container-fluid {
    background-color: $header-background;
  }

  .header {
    margin-bottom: 80px;
    padding: 100px 0 100px;
  }

  h1 {
    .lastname {
      font-weight: normal !important;
    }
  }

  .header-subtitle {
    color: $white;
    position: relative;
    text-align: left;
    margin-bottom: 50px;

    &::after {
      content: "";
      background: $orange;
      height: 5px;
      width: 700px;
      position: absolute;
      bottom: -20px;
      left: -500px;

      @media(min-width: 360px) {
        left: -400px;
      }
    }
  }

  .dot {
    color: $white;
    display: none;

    @media(min-width: 360px) {
      display: inline;
    }
  }

  .imageHeader {
    img {
      width: 100%;
    }
  }

  .socials {
    margin-bottom: 20px;

    a {
      display: inline-block;
      margin-bottom: 10px;
      text-decoration: none;

      &.outline {
        background: none;
        border: 2px solid $orange;
        border-radius: 5px;
        padding: 7px 20px;
        margin-right: 15px;
        color: $orange;
        transition: .3s;

        &:hover {
          background: $orange;
          color: #1a1a2e;
        }
      }

      &.filled {
        background: $orange;
        border: 2px solid $orange;
        border-radius: 5px;
        padding: 7px 20px;
        margin-right: 15px;
        color: #1a1a2e;
        box-shadow: 0px 6px 7px $shadow;
        transition: .3s ease-out;

        &:hover {
          box-shadow: none;
          transform: scale(1.1);
          transition: .3s ease;
        }
      }
    }
  }
</style>
