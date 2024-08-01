<template>
<div>
    <v-row>
        <v-col cols="3" sm="3" v-for="(Popular,i) in Populars" :key="i">
            <v-card class="mx-auto my-4 pb-4" maximum-width="374">
                <v-img  height="250"  class="mx-4" :src="Popular.img"></v-img>
                <v-card-items class="mt-n4">
                    <v-card-title class="text-center">{{ Popular.title }}</v-card-title>
                </v-card-items>
                <v-card-text >
                    <div class="text-center">{{ Popular.bio }}</div>
                    <v-row align="center" class="mx-0 mt-2" >
                        <v-rating :model-value="4.5" color="amber" density="compact" half-increments readonly size="small" >
                        </v-rating>
                        <v-spacer></v-spacer>
                    </v-row>
                </v-card-text>
            </v-card>
        </v-col>
    </v-row>
</div>
</template>

<script>
export default{
    data(){
        return{
            Populars:[
                {
                    img:"",
                    title:"",
                    price:"",
                    bio:""
                },
                {
                    img:"",
                    title:"",
                    price:"",
                    bio:""
                },
                {
                    img:"",
                    title:"",
                    price:"",
                    bio:""
                },
                {
                    img:"",
                    title:"",
                    price:"",
                    bio:""
                },
            ]
        }
    }
}
</script>

<style>
</style>