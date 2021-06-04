<template>
  <div class="contactForm container" id="contact">
    <form>
      <div class="text">
        <p class="subtitle">Contact me</p>
        <hr>
        <h2 v-if="!isDisabled">Let's talk so that we can make it all start happening.</h2>

        <p
        v-if="page.content"
        v-html="page.content.rendered"
        class="subtitle"
        >
        </p>

        <p v-if="isDisabled" class="thankyou">
          Thank you for your message, I'll reply as soon as possible
        </p>
      </div>


      <div v-if="!isDisabled" class="row">
        <div class="col-12 col-md-6">
          <div class="form-group">
            <input class="form-control" type="text" placeholder="Name" v-model="form.fullname" required>
          </div>
        </div>

        <div class="col-12 col-md-6">
          <div class="form-group">
            <input class="form-control" type="email" placeholder="Email" v-model="form.email" required>
          </div>
        </div>

        <div class="col-12">
          <div class="form-group">
            <textarea class="form-control" rows="3" placeholder="Enter you message here" v-model="form.message" required></textarea>
          </div>
        </div>
      </div>

      <div v-if="!isDisabled" class="col-12 text-center">
        <button
          type="submit"
          class="btn btn-primary"
          :disabled="isDisabled"
          @click.prevent="submitForm">
            Send <img :src="sendSVG" />
        </button>
      </div>
    </form>
  </div>
</template>

<script>
  import axios from 'axios';
  import sendSVG from "@/assets/send.svg";

  export default {
    name: 'ContactForm',
    data() {
      return {
        pageUrl: "https://wp.marthesselink.nl/wp-json/wp/v2/pages?id=188",
        page: [],
        formUrl: "https://wp.marthesselink.nl/wp-json/contact-form-7/v1/contact-forms/164/feedback",
        form: {
          fullname: '',
          email: '',
          message: ''
        },
        isDisabled: false,
        errors: [],
        sendSVG
      };
    },
    methods : {
      submitForm() {
        var FormData = require('form-data');
        var data = new FormData();

        data.append('fullname', this.form.fullname);
        data.append('email', this.form.email);
        data.append('message', this.form.message);
        this.isDisabled = true;

        if (this.form.fullname && this.form.email && this.form.message) {
          axios
            .post(this.formUrl, data, {
              headers: {
                'Content-Type': 'multipart/form-data'
              }
            })
            .then(response => {
              console.log(response);

              if (response.status === 200) {
                this.form.fullname = '';
                this.form.email = '';
                this.form.message = '';
                this.isDisabled = true;
              }
            })
            .catch(error => {
              console.log(error);
            });
        } else {
          alert('Uh oh, you forgot some fields.. Please try again');
          this.isDisabled = false;
        }
      },
      getPageData() {
        axios
          .get(this.pageUrl)
          .then(response => {
            this.page = response.data[0];
            console.log('Page data retrieved! contact');
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

<style lang="scss" scoped>
  .contactForm {
    margin-bottom: 40px;
    padding-left: 15px;
    padding-right: 15px;

    h2 {
      color: $white;
      font-size: 40px;
    }

    .subtitle {
      text-align: center;
    }

    .thankyou {
      color: $white;
      font-weight: bold;
      font-size: 30px;
    }

    input,
    textarea {
      padding: 25px;
      background-color: $form;
      border: 0;
      margin-bottom: 30px;
      color: $grey;
      font-size: 20px;
      font-style: normal;
      font-weight: 400;
      line-height: 25px;
      letter-spacing: 0em;
      text-align: left;
    }

    input {
      &::placeholder {
        color: $grey;
      }
    }

    .btn {
      min-width: 300px;
      margin: 0 auto;
      padding: 20px;
      background-color: $orange;
      color: $header-background;
      border: 0;
      font-weight: 500;
      font-size: 24px;
      line-height: 126.9%;

      img {
        height: 15px;
        vertical-align: baseline;
        margin-left: 5px;
      }
    }
  }
</style>
