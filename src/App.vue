<template>
  <v-app>
    <v-main>
      <div>
      <div class="header-view" v-show="isDesktop">
      <AllView/>
    </div>
    <div class="mobile-view" v-show="!isDesktop">
      <MobileView />
    </div>
    </div>
    </v-main>
  </v-app>
  <!-- <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </nav> -->
  <router-view/>
</template>

<script>
import MobileView from './views/MobileView.vue';
import AllView from '@/views/AllView.vue';
export default{
  name: 'App',
  components:{
    MobileView,
    AllView,
  },
  // beforeMount() {
  //   this.fetchData();
  //   this.checkLoggedIn();
  // },
  mounted() {
    this.checkScreenSize();
    window.addEventListener('resize', this.checkScreenSize);
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.checkScreenSize);
  },
  methods:{
    checkScreenSize() {
      this.isDesktop = window.innerWidth >= 960; // or whatever breakpoint you consider for medium and up
    },
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
.header-view {
  display: none;
}

.mobile-view {
  display: block;
}

@media (min-width: 960px) {
  .header-view {
    display: block;
  }
  .mobile-view {
    display: none;
  }
}
</style>
