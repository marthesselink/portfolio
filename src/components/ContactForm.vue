<template>
  <div class="contactForm" id="contact">
    <form>
      <h2>Contact</h2>

      <p
        v-if="page.content"
        v-html="page.content.rendered"
        class="subtitle"
      >
      </p>

      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <input class="form-control" type="text" placeholder="Default input" v-model="form.fullname" required>
          </div>

          <div class="form-group">
            <input class="form-control" type="email" placeholder="name@example.com" v-model="form.email" required>
          </div>
        </div>

        <div class="col-md-6">
          <div class="form-group">
            <textarea class="form-control" rows="3" v-model="form.message" required></textarea>
          </div>
        </div>
      </div>


      <button type="submit" class="btn btn-primary w-100" @click.prevent="submitForm">Send</button>
    </form>
  </div>
</template>

<script>
  import axios from 'axios';

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
        errors: []
      };
    },
    methods : {
      submitForm() {
        var FormData = require('form-data');
        var data = new FormData();

        data.append('fullname', this.form.fullname);
        data.append('email', this.form.email);
        data.append('message', this.form.message);

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
                alert("Thank you for your message, I'll reply as soon as possible");

                this.form.fullname = '';
                this.form.email = '';
                this.form.message = '';
              }
            })
            .catch(error => {
              console.log(error);
            });
        } else {
          alert('Uh oh, you forgot some fields.. Please try again');
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

    .subtitle {
      text-align: center;
    }
  }
</style>
