<template>
  <v-app>
    <NavBar />
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="12" sm="12">
            <ClientSec/>
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12" sm="12">
            <!-- <v-carousel>
              <v-carousel-item
                v-for="(item, i) in items"
                :key="i"
                :src="item.src"
                cover
              >
                <v-row>
                  <v-col cols="12" sm="6">
                    <div class="d-flex fill-height justify-center align-center">
                      <h2 class="text-white top">{{ item.title }}</h2>
                      <br />
                    </div>
                    <div class="d-flex fill-height justify-center align-center">
                      <p class="text text-white">{{ item.text }}</p>
                    </div>
                    <div class="d-flex fill-height justify-center align-center">
                      <v-btn style="margin-top: -120px">Buy Now</v-btn>
                    </div>
                  </v-col>
                </v-row>
              </v-carousel-item>
            </v-carousel> -->
          </v-col>
          <v-toolbar color="transparent" class="PopularProduct">
            <v-toolbar-title><h3>Popular Mobiles Top Campanies </h3></v-toolbar-title>

            <!-- <v-spacer></v-spacer>
            <v-btn icon="mdi mdi-chevron-left"></v-btn>
            <v-btn icon="mdi mdi-chevron-right"></v-btn> -->
          </v-toolbar>
          <v-col cols="12" sm="12" class="mt-10">
            <PopularPro />
          </v-col>
          <v-toolbar color="transparent" class="mt-10">
            <v-toolbar-title><h3>Top Three Sumsung Mobiles</h3></v-toolbar-title>

            <!-- <v-spacer></v-spacer>
            <v-btn icon="mdi mdi-chevron-left"></v-btn>
            <v-btn icon="mdi mdi-chevron-right"></v-btn> -->
          </v-toolbar>
          <v-col cols="12" sm="12" class="mt-10">
            <FeaturePro/>
          </v-col>
          <v-toolbar color="transparent" class="mt-10">
            <v-toolbar-title><h3>Top Three Apple Mobiles</h3></v-toolbar-title>
          </v-toolbar>
          <v-col cols="12" sm="12" class="mt-10">
            <AppleMobile/>
          </v-col>
          <v-col cols="12" sm="12" class="app mt-10" >
            <ClientSec />
          </v-col>

          <v-col cols="12" sm="12" class="mt-10">
            <v-row>
              <v-col cols="3" sm="4">
                <v-card class="mx-auto my-12 pb-4" max-width="374">
                  <v-row>
                    <v-col cols="12" sm="6">
                      <v-card-item class="mt-10">
                        <v-card-title class="text-center"
                          >Smart watch</v-card-title
                        >
                      </v-card-item>

                      <v-card-text>
                        <div class="text-center">
                          Small plates, salads & sandwiches
                        </div>
                        <div class="text-center mt-4">
                          <v-btn color="black">Buy Now</v-btn>
                        </div>
                      </v-card-text>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-img
                        height="250"
                        class="mx-4"
                        src="13.jpg"
                      ></v-img>
                    </v-col>
                  </v-row>
                </v-card>
              </v-col>
              <v-col cols="3" sm="4">
                <v-card class="mx-auto my-12 pb-4" max-width="374" color="red">
                  <v-row>
                    <v-col cols="12" sm="6">
                      <v-card-item class="mt-10">
                        <v-card-title class="text-center"
                          >Smart watch</v-card-title
                        >
                      </v-card-item>

                      <v-card-text>
                        <div class="text-center">
                          Small plates, salads & sandwiches
                        </div>
                        <div class="text-center mt-4">
                          <v-btn color="black">Buy Now</v-btn>
                        </div>
                      </v-card-text>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-img
                        height="250"
                        class="mx-4"
                        src="14.jpg"
                      ></v-img>
                    </v-col>
                  </v-row>
                </v-card>
              </v-col>
              <v-col cols="3" sm="4">
                <v-card class="mx-auto my-12 pb-4" max-width="374">
                  <v-row>
                    <v-col cols="12" sm="6">
                      <v-card-item class="mt-10">
                        <v-card-title class="text-center"
                          >Smart watch</v-card-title
                        >
                      </v-card-item>

                      <v-card-text>
                        <div class="text-center">
                          Small plates, salads & sandwiches
                        </div>
                        <div class="text-center mt-4">
                          <v-btn color="black">Buy Now</v-btn>
                        </div>
                      </v-card-text>
                    </v-col>
                    <v-col cols="12" sm="6">
                      <v-img
                        height="250"
                        class="mx-4"
                        src="15.jpg"
                      ></v-img>
                    </v-col>
                  </v-row>
                </v-card>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
      <FooterSection />
    </v-main>
  </v-app>
</template>

<script setup>
import NavBar from "@/components/NavBar.vue";
import FooterSection from "@/components/FooterSection.vue";
import PopularPro from "@/components/PopularPro.vue";
import FeaturePro from "@/components/FeaturePro.vue";
import ClientSec from "@/components/ClientSec.vue";
import AppleMobile from "@/components/AppleMobile.vue";
</script>
<script>
export default {
  data() {
    return {
      // items: [
      //   {
      //     src: "2.jpg",
      //     title: "Surface Studio",
      //     text: "Le lorem ipsum est, en imprimerie, une suite de mots sans signification utilisée à titre provisoire pour calibrer une mise en page, le texte définitif venant remplacer le faux-texte dès ",
      //   },
      //   {
      //     src: "3.jpg",
      //     title: "Surface Studio",
      //     text: "Le lorem ipsum est, en imprimerie, une suite de mots sans signification utilisée à titre provisoire pour calibrer une mise en page, le texte définitif venant remplacer le faux-texte dès ",
      //   },
      //   {
      //     src: "1.jpg",
      //     title: "Surface Studio",
      //     text: "Le lorem ipsum est, en imprimerie, une suite de mots sans signification utilisée à titre provisoire pour calibrer une mise en page, le texte définitif venant remplacer le faux-texte dès ",
      //   },
      //   {
      //     src: "7.jpg",
      //     title: "Surface Studio",
      //     text: "Le lorem ipsum est, en imprimerie, une suite de mots sans signification utilisée à titre provisoire pour calibrer une mise en page, le texte définitif venant remplacer le faux-texte dès ",
      //   },
      //   {
      //     src: "5.jpg",
      //     title: "Surface Studio",
      //     text: "Le lorem ipsum est, en imprimerie, une suite de mots sans signification utilisée à titre provisoire pour calibrer une mise en page, le texte définitif venant remplacer le faux-texte dès ",
      //   },
      // ],
    };
  },
};
</script>
<style scoped>
/* .app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
.top {
  margin-top: 100px;
}
.text {
  margin-top: -40px;
  margin-left: 80px;
}
.top-day {
  margin-top: 120px;
}
</style>
