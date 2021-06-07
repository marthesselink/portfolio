<template>
  <nav class="navbar fixed-top navbar-expand-md navbar-dark bg-dark">
    <div class="container">
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
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="collapse">
        <ul class="navbar-nav ms-auto">
          <li class="nav-item active">
            <a class="nav-link" aria-current="page" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#github">Open Source</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#projects">Projects</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">Contact</a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
  export default {
    name: 'Navbar',
    mounted() {
      const navLinks = document.querySelectorAll('.nav-item')
      const menuToggle = document.getElementById('collapse')

      navLinks.forEach((l) => {
        l.addEventListener('click', () => {
          menuToggle.classList.remove('show');
        })
      })
    }
  }
</script>

<style lang="scss" scoped>
  .bg-dark {
    background-color: $header-background !important;
    opacity: 0.95;
  }

  .navbar {
    .navbar-brand {
      color: $white;
      font-size: 24px;
    }

    .nav-item {
      color: $grey;

      &:hover {
        color: $orange;
      }
    }

    .active {
      color: $orange !important;
    }

    .navbar-collapse {
      .navbar-nav {
        height: 100vh;
        text-align: center;
        font-size: 25px;

        @media(min-width: 768px) {
          text-align: left;
          height: 50px;
          font-size: inherit;
        }
      }
    }

    .navbar-toggler {
      border: 0;
    }
  }
</style>