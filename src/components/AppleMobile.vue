<template>
  <v-row justify="center" class="space px-16">
    <v-col cols="12" xs="12" sm="6" md="4" v-for="(Image, i) in Images" :key="i">
      <v-card class="mx-auto rounded-xl" max-width="400" :elevation="5" outlined style="border: 1px solid black;">
        <v-row no-gutters align="center">
          <v-col cols="5">
            <v-img class="img" max-height="150" contain :src="Image.img"></v-img>
          </v-col>
          <v-col cols="7">
            <v-card-title class="title">{{ Image.title }}</v-card-title>
            <v-card-subtitle class="grey--text text-grey-darken-1 subtitle">{{ Image.subtitle }}</v-card-subtitle>
            <v-card-text class="price">{{ Image.price }}</v-card-text>
            <v-btn class="mt-2 mb-2" style="background-color: orange; border-radius: 15px; width: 70%; font-size: 10px;">Buy Now</v-btn>
          </v-col>
        </v-row>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    bpm: 1,
    Images: [
      { img: "i14.png", title: "Apple", subtitle: "Iphone 14", price: "Rs: $1340",},
      { img: "i13.png", title: "Apple ", subtitle: "13 Pro Max", price: "Rs: $1200",  },
      { img: "i12.png", title: "Apple", subtitle: "Iphone 12", price: "Rs: $980", },
    ],
  }),
  // methods: {
  //   increment(Image) {
  //     Image.bpm++;
  //   },
  //   decrement(Image) {
  //     if (Image.bpm > 0) {
  //       Image.bpm--;
  //     }
  //   },
  // },
};
</script>

<style>
.img {
  width: 100%;
  height: auto;
}
.title {
  font-size: large;
  color: black;
  font-weight: 900;
}
.subtitle {
  font-size: medium;
  color: black;
  font-weight: 700;
}
.price {
  font-size: medium;
  color: black;
  font-weight: 700;
}
</style>
