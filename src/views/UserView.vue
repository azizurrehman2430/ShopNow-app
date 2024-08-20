<template>
    <v-app>
      <v-main class="mt-16">
          <h1 align="center" justify="center" class="mt-6 ">
             UsersData
          </h1>  
         <UserData/>
          </v-main>
      </v-app>

  </template>
<script>
import UserData from '../components/UserData.vue';

export default {
  name: 'UsersView',

  components: {
    UserData,
  },
};
</script>
