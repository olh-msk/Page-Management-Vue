<template>
  <nav
    :class="[`navbar-${theme}`, `bg-${theme}`, 'navbar', 'navbar-expand-lg']"
  >
    <div class="container-fluid">
      <a class="navbar-brand" href="#">My Vue!</a>
      <ul class="navbar-nav me-auto nb-2 mb-lg-0">
        <li v-for="(page, index) in pages" class="nav-item" :key="index">
          <navbar-link
            :page="page"
            :isActive="activePage === index"
            @click.prevent="navLinkClick(index)"
          ></navbar-link>
        </li>
      </ul>
      <form class="d-flex">
        <button class="btn btn-primary" @click.prevent="changeTheme()">
          {{ useDarkNavbar ? 'Light' : 'Dark' }} mode
        </button>
      </form>
    </div>
  </nav>
</template>

<script>
import NavbarLink from './NavbarLink.vue';
export default {
  components: {
    NavbarLink,
  },
  props: ['pages', 'activePage', 'navLinkClick'],

  data() {
    return {
      theme: 'light',
      useDarkNavbar: false,
    };
  },
  methods: {
    changeTheme() {
      let theme = 'light';
      if (this.theme == 'light') {
        theme = 'dark';
      }
      this.useDarkNavbar = !this.useDarkNavbar;
      this.theme = theme;
    },
  },
};
</script>
