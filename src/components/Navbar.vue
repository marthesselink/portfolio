<template>
  <nav class="navbar fixed-top navbar-expand-md navbar-light bg-white">
    <a class="navbar-brand" href="#">
      <img src="../assets/logo.png" width="30" height="30" class="d-inline-block align-top" alt="">
      Mart Hesselink
    </a>
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target=".collapse"
      aria-controls="collapse"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
    </button>
    <div class="collapse navbar-collapse">
      <div class="navbar-nav ml-auto">
        <a class="nav-item nav-link active" href="#">Home <span class="sr-only">(current)</span></a>
        <a class="nav-item nav-link" href="#github">Open Source</a>
        <a class="nav-item nav-link" href="#projects">Projects</a>
        <a class="nav-item nav-link" href="#contact">Contact</a>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    name: 'Navbar',
  }
</script>

<style lang="scss" scoped>
  .navbar {
    $p: &;

    max-width: 1140px;
    margin: 0 auto;
    padding: 10px 40px;

    .navbar-toggler {
      &:active, &:focus {
        outline: 0;
      }

      .icon-bar {
        background: black;
        display: block;
        width: 22px;
        height: 2px;
        border-radius: 1px;
        margin: 4px 0 4px 0;
        transition: all 0.2s;

        /* .navbar closed top .icon-bar no rotation - straight */
        &:nth-of-type(1) {
            transform: rotate(0);
          }

          /* .navbar open middle .icon-bar visible */
          &:nth-of-type(2) {
            opacity: 1;
            filter: alpha(opacity=100);
          }

          /* .navbar open bottom .icon-bar no rotation - straight */
          &:nth-of-type(3) {
            transform: rotate(0);
          }
      }
    }

    @at-root .show#{&} {
      .icon-bar {
        /* .navbar open top .icon-bar rotated down 45° */
        &:nth-of-type(1) {
          transform: rotate(45deg);
          transform-origin: 10% 10%;
        }

        /* .navbar open middle .icon-bar invisible */
        &:nth-of-type(2) {
          opacity: 0;
          filter: alpha(opacity=0);
        }

        /* .navbar open bottom .icon-bar rotated up 45° */
        &:nth-of-type(3) {
          transform: rotate(-45deg);
          transform-origin: 10% 90%;
        }
      }
    }

    .navbar-collapse {
      transition: all .2s ease-out;
      height: 100vh;

      @media(min-width: 768px) {
        height: 60px;
      }

      .navbar-nav {
        margin-top: 40px;
        text-align: center;
        font-size: 25px;

        @media(min-width: 768px) {
          margin-top: 0;
          text-align: left;
          font-size: inherit;
        }
      }
    }

    .navbar-toggler {
      border: 0;
    }
  }
</style>