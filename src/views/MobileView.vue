<template>
    <v-app>
      <v-app-bar class="bar" height="80px" flat color="primary">
        <strong><span class="ml-4">Shop</span><span style="color: orange">Now</span></strong>
        <v-spacer></v-spacer>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="mr-4">
        </v-app-bar-nav-icon>
      </v-app-bar>
      <v-navigation-drawer v-model="drawer" app temporary class="bar">
        <v-list-item>
          <v-list-item-avatar>
            <!-- <v-img :src="require('@/assets/logo.png')" height="30px"
    width="30px"
    contain></v-img> -->
          </v-list-item-avatar>
        </v-list-item>
        <v-divider></v-divider>
        <v-list-item-group>
          <v-list>
            <v-list-item
              v-for="link in links"
              :key="link.id"
              :to="link.route"
              :ripple="false"
              class="routelinks"
            >
              <v-icon>{{ link.icon }}</v-icon>
              <span class="ml-4">{{ link.name }}</span>
            </v-list-item>
          </v-list>
        </v-list-item-group>
      </v-navigation-drawer>
        <router-view></router-view>
        <FooterSection/>
    </v-app>
  </template>
  
  <script>
  import FooterSection from'@/components/FooterSection.vue'
  export default {
    name: "MobileView",
  components:{
    FooterSection
  },
    data: () => ({
      drawer: false,
      links: [
        { name: "HomeView", route: "/", icon: "mdi-home" },
        { name: "Products", route: "/about", icon: "mdi-information" },
        { name: "Services", route: "/services", icon: "mdi-newspaper-variant" },
        { name: "Users", route: "/users", icon: "mdi-note-edit" },
        { name: "Contact Us ", route: "/contact-us", icon: "mdi-chevron-right" },
      ],
    }),
    watch: {
      group() {
        this.drawer = false;
      },
    },
  };
  </script>
  <style scoped>
  
  /* .v-list-item {
    text-decoration: none;
    } */
  .bar {
    background:rgb(204, 246, 248);
  }
  .routelinks {
  font-weight: bold;
  color: black;
  text-decoration:dashed; /* Remove underline */
  padding: 6px 20px; /* Add padding to make it look like a button */
  border: 2px solid black; /* Add a border */
  border-radius: 5%; /* Rounded corners */
  background-color: rgb(251, 250, 250); /* Background color */
  transition: background-color 0.3s, color 0.3s; /* Smooth transition */
  /* display: inline-block; Make it inline-block to respect padding and margin */
}

.routelinks:hover {
  background-color:black; /* Change background color on hover */
  color: white; /* Change text color on hover */
}
  </style>