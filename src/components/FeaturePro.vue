<template>
  <v-row justify="center" class="space px-16">
    <v-col cols="12" xs="12" sm="6" md="4" v-for="(feature, i) in features" :key="i">
      <v-card class="mx-auto rounded-xl"  max-width="300" :elevation="5" color="" flat outlined style="border: 1px solid black;">
        <div align="center" justify="center">
          <v-img class="img mt-4" max-height="300" max-width="300" contain :src="feature.img"></v-img>
        </div>

        <v-card-title class="title">{{ feature.title }}</v-card-title>
        <v-card-title class="grey--text text-grey-darken-1 caption mt-n2" id="subtitle">{{feature.subtitle}}</v-card-title>
        <v-card-title class="mt-n4" id="price">{{ feature.price }}</v-card-title>

        <v-card-actions class="mx-16 mt-1" style="justify-content: center;">
          <v-btn outlined class="mt-n2 add small-btn bordered-btn" @click="decrement(feature)">
            <v-icon color="green">mdi-minus</v-icon>
          </v-btn>
          <strong class="mx-2">{{ feature.bpm }}</strong>
          <v-btn outlined class="mt-n2 add small-btn bordered-btn" @click="increment(feature)">
            <v-icon color="green">mdi-plus</v-icon>
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>
<script>
export default{
    data: () => ({
    bpm: 1,
    features: [
      { img: "SZF6.png", title: "Sumsung Galaxy", subtitle: "Z Fold 6", price: "Rs: $1900",bpm:1 },
      { img: "s24.png", title: "Sumsung ", subtitle: "Galaxy s23 Ultra", price: "Rs: $1000", bpm:1 },
      { img: "SBF.png", title: "Sumsung", subtitle: " Blue Flip", price: "Rs: $1000",bpm:1 },
    ],
  }),
  methods: {
    increment(feature) {
      feature.bpm++;
    },
    decrement(feature) {
      if (feature.bpm > 0) {
        feature.bpm--;
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
  color: green;
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
  color: green;
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