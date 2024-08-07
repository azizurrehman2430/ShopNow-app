<template>
  <v-row justify="center" class="space px-16">
    <v-col cols="12" xs="12" sm="6" md="4" v-for="(product, i) in products" :key="i">
      <v-card class="mx-auto rounded-xl" max-width="300" :elevation="5" color="" flat outlined style="border: 1px solid;">
        <div align="center" justify="center">
          <v-img class="img" max-height="320" max-width="320" contain :src="product.img"></v-img>
        </div>

        <v-card-title style="color: black;" class="title">{{ product.title }}</v-card-title>
        <v-card-title class="grey--text text-grey-darken-1 caption mt-n6" id="subtitle">{{product.subtitle}}</v-card-title>
        <v-card-title style="color: black;" class="mt-n4" id="price">{{ product.price }}</v-card-title>

        <v-card-actions class="mx-16 mt-1" style="justify-content: center; ;">
          <v-btn outlined class="mt-n2 add small-btn bordered-btn" @click="decrement(product)">
            <v-icon color="green">mdi-minus</v-icon>
          </v-btn>

          <strong class="mx-2">{{ product.bpm }}</strong>
          <v-btn outlined class="mt-n2 add small-btn bordered-btn" @click="increment(product)">
            <v-icon color="green">mdi-plus</v-icon>
          </v-btn>
          <!-- <v-spacer></v-spacer>
          <v-btn class="mx-2 mt-n3 shopping" fab dark small color="green">
            <v-icon dark> mdi-shopping </v-icon>
          </v-btn> -->
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    bpm: 1,
    products: [
      { img: "i1.png", title: "IPhone ", subtitle: "15 pro max", price: "Price: $1000", bpm:1 },
      { img: "s24.png", title: "Sumsung Galaxy", subtitle: "S24 Ultra", price: "Price: $1000",bpm:1 },
      { img: "vY35.png", title: "Vivo", subtitle: "Y35", price: "Price: $280",bpm:1 },
      { img: "TC20.png", title: "Tecno", subtitle: "Camon20 Prime 5G", price: "Rs: $450",bpm:1 },
      { img: "Gp8a.png", title: "Google", subtitle: "Pixel 8a", price: "Rs: $500",bpm:1 },
      { img: "RN63.png", title: "Realme", subtitle: "Narzo 63", price: "Rs: $200",bpm:1},
    ],
  }),
  methods: {
    increment(product) {
      product.bpm++;
    },
    decrement(product) {
      if (product.bpm > 0) {
        product.bpm--;
      }
    }

  },
};
</script>

<style>
.img{
  width: 80%;
  height: 80vh;
}
.title {
  margin-top: 23px;
  margin-bottom: 5px;
  font-size: x-large;
  color: black;
  font-weight: 900;
  text-align: center;
}

#subtitle {
  font-size: large;
  color: green;
  font-weight: 900;
  text-align: center;
}

#price {
  font-size: large;
  color:black;
  font-weight: 900;
  text-align: center;
}

.green-border {
  border: 2px solid green;
}

.small-btn {
  padding: 0 !important;
  min-width: 32px !important;
  width: 32px !important;
  height: 32px !important;
}
.bordered-btn {
  border: 2px solid green !important;
  border-radius: 50%;
 
}
.shopping{
  margin-top: 10px;
  font-size: large; 
}
</style>