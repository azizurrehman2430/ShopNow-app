<template>
  <v-app>
    <NavBar/>
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="12" sm="12" >
            <v-carousel>
              <v-carousel-item v-for="( item, i ) in items" :key="i" :src="item.src" cover> 
              <v-row>
                <v-col cols="12" sm="6" >
                  <div class=" d-flex fill-height justify-center align-center">
                    <h2 class="text-white top">{{ item.title }}</h2><br>
                  </div>
                  <div class=" d-flex fill-height justify-center align-center">
                    <p class="text text-white ">{{ item.text }}</p>
                  </div>
                  <div class=" d-flex fill-height justify-center align-center">
                    <v-btn style="margin-top: 20px; color: red;">Buy Now</v-btn>
                  </div>
                </v-col>
              </v-row>
            </v-carousel-item>
            </v-carousel>
          </v-col>
          <v-toolbar color="transparent">
            <v-toolbar-title>
              Popular Products
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn icon="mdi mdi-chevron-left"></v-btn>
            <v-btn icon="mdi mdi-chevron-right"></v-btn>
          </v-toolbar>
          <v-col cols="12" sm="12" class="mt-10">
            <PopularPro/>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </v-app>
</template>
<script>
import NavBar from '@/components/NavBar.vue';
import PopularPro from '@/components/PopularPro.vue'
export default {
  name:'HomeView',
  components:{
    NavBar,
    PopularPro
  },
  data(){
    return{
      items:[
        {src:'https://picsum.photos/200/300',
          title: "Surface Studio",
          text: "lorem"
        },
        {src:'https://picsum.photos/400/500',
          title: "Surface Studio",
          text: "lorem"
        },{src:'https://picsum.photos/500/500',
          title: "Surface Studio",
          text: "lorem"
        },
      ]
    }
  }
}
</script>
<style scoped>
O references
.top{
  margin-top:100px;
}
O references
.text{
  margin-top:-40px;
  margin-left:80px;
}
O references
.top-day{
  margin-top:120px;
}
</style>