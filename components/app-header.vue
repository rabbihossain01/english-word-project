<template>
  <nav class="navbar" :style="{ boxShadow: shadow }">
    <div class="container">
      <div class="nav-logo">
        <p>Logo will be here</p>
      </div>
      <ul class="nav_list">
        <li><a href="#landing">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="#company-section">Company</a></li>
        <li><a href="#pricing-cards">Pricing</a></li>
        <li><a href="#contact-section">Contact</a></li>
        <button class="btn">Login</button>
      </ul>
      <div class="dopdownmenu">
        <img
          src="icon-image/outline_menu.png"
          alt="menu-image"
          width="30"
          @click="showMenu = !showMenu"
        />
      </div>
    </div>
    <div v-if="showMenu" class="mobile-menu">
      <a href="#landing">Home</a>
      <a href="/about">About</a>
      <a href="#company-section">Company</a>
      <a href="#pricing-cards">Pricing</a>
      <a href="#contact-section">Contact</a>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      shadow: true,
      showMenu: false,
    }
  },
  mounted() {
    document.body.onscroll = () => {
      if (window.scrollY > 0) {
        this.shadow = '0 3px 4px 0 rgba(0, 0, 0, 0.1)'
      }
      if (window.scrollY < 10) {
        this.shadow = 'unset'
      }
    }
  },
}
</script>

<style lang="scss" scoped>
@import '~/styles/style.scss';

.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background-color: $nav-background-color;
  z-index: 9;

  .container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    @extend .main-container;
    padding: 20px 10px 20px 10px;

    .nav-logo {
      svg {
        cursor: pointer;
      }
    }

    .nav_list {
      display: flex;
      justify-content: space-between;
      align-items: center;
      li {
        list-style: none;
        a {
          text-decoration: none;
          color: $link-text-color;
          font-size: $link-font-size;
          font-weight: 500;
          padding: 10px;
          transition: 0.3s;

          &:hover {
            color: #16171a;
          }
        }
      }

      .btn {
        @extend .btn-primary;
        padding: 10px 20px;
        font-size: 14px;
        font-weight: 300;
      }
    }
  }
  .dopdownmenu {
    display: none;
  }
  .mobile-menu {
    @extend .main-container;
    a {
      display: block;
      color: $primary-color;
      padding: 10px 12px;
      text-decoration: none;
      font-size: $link-font-size;
      background-color: $bg-primary;
      &:hover {
        background-color: #ddd;
        color: black;
      }
    }
  }
}

@include responsive(phone) {
  .navbar {
    .container {
      .nav_list {
        display: none;
      }
      .dopdownmenu {
        display: block !important;
        justify-self: end;
        align-self: center;
      }
    }
  }
}
</style>
