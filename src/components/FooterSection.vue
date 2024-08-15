<template>
  <v-footer dark padless class="footer">
    <v-card flat tile class="black white--text py-12 px-5 footer " width="100%">
      <v-row>
        <v-col cols="12" xs="12" sm="6" md="4" class="pa-16">
          <v-toolbar color="transparent" flat>
          <!-- <v-badge color="#D5F0DB" dot>
           <v-img src="sh1.png" contain width="10"></v-img>
          </v-badge> -->

            <v-toolbar-title class="">
              <strong class="heading">Shop<span style="color: orange">Now</span></strong>
            </v-toolbar-title>
          </v-toolbar>
          <div class="icon ml-1">
            <v-btn icon href="https://www.facebook.com/profile.php?id=100074228396400&mibextid=ZbWKwL" target="blank"
              class="mt-6 mr-2 face">
              <v-icon size="20" color="blue-darken-2">mdi-facebook</v-icon>
            </v-btn>
            <v-btn icon href="https://github.com/azizurrehman2430" target="blank" class="mt-6 mr-2">
              <v-icon size="20" center>mdi-github</v-icon>
            </v-btn>
            <v-btn icon href="https://www.linkedin.com/in/aziz-ur-rehman-637008247/" target="blank" class="mt-6 mr-2">
              <v-icon size="20" color="blue">mdi-linkedin</v-icon>
            </v-btn>
            <v-btn icon href="https://www.instagram.com/rai_aziz24?utm_source=qr&igsh=MW02YzVoc2JpbnExaQ=="
              target="_blank" class="mt-6 mr-2">
              <v-icon size="20" color="red">mdi-instagram</v-icon>
            </v-btn>
          </div>
        </v-col>
        <v-col cols="12" xs="12" sm="6" md="2">
          <v-card-text class="white--text pt-0">
            <h3 class="heading">About</h3>
          </v-card-text>
          <v-card-text class="grey--text"> How it Work</v-card-text>
          <v-card-text class="grey--text mt-n4"> Our Programs </v-card-text>
          <v-card-text class="grey--text mt-n4"> Promotions </v-card-text>
          <v-card-text class="grey--text mt-n4"> Refer A Friend </v-card-text>
        </v-col>
        <v-col cols="12" xs="12" sm="6" md="2">
          <v-card-text class="white--text pt-0">
            <h3 class="heading">Dellvery</h3>
          </v-card-text>
          <v-card-text class="grey--text"> Cost of Delevery </v-card-text>
          <v-card-text class="grey--text mt-n4"> Payment Method </v-card-text>
          <v-card-text class="grey--text mt-n4"> Delevery Astus </v-card-text>
          <v-card-text class="grey--text mt-n4"> Returns </v-card-text>
        </v-col>
        <v-col cols="12" xs="12" sm="6" md="4">
          <v-card-text class="white--text pt-0">
            <h3 class="heading">Contact</h3>
          </v-card-text>
          <v-card-text class="grey--text "> Punjab,Pakistan. </v-card-text>
          <v-card-text class="grey--text mt-n4"> azizurrehman2430@gmail.com </v-card-text>
          <v-card-text class="grey--text mt-n4">
            +92 318-4842724
          </v-card-text>
          <v-card-text class="grey--text mt-n4"> +92 323-2848024 </v-card-text>
        </v-col>
      </v-row>
    </v-card>
  </v-footer>
</template>

<script>
export default {
  data: () => ({

  }),
};
</script>

<style>
.footer {
  background-color: rgb(39, 38, 38);
}

.icon {
  display: flex;
}

.heading {
  color: white;
}

.green--text {
  color: green !important;
}

.grey--text {
  color: gray !important;
}
</style>