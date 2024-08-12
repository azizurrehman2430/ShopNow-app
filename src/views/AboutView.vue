<template>
 <v-app>
  <v-main>
    <v-col cols="12" sm="12">
      <PopularPro/>
    </v-col>
  </v-main>
 </v-app>
</template>
<script>
import PopularPro from '@/components/PopularPro.vue'
export default{
  name:"PopularPro",
  components:{
    PopularPro
  }
}
</script>