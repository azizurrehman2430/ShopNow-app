<template>
    <v-app-bar flat style=" background: linear-gradient(to right, #00aaff, #f9d423 );">
        <template v-slot:prepend>
            <v-app-bar-nav-icon>
            </v-app-bar-nav-icon>
        </template>
        <v-app-bar-title><h4><span style="color: red;">Shop</span>Now</h4></v-app-bar-title>
        <v-spacer></v-spacer>
        <v-text-field density="compact" variant="solo" label="search products" append-inner-icon="mdi-magnify"
            single-line hide-details flat></v-text-field>
            <!-- <v-spacer></v-spacer> -->
            <v-btn>Sign in/Login</v-btn>
        <router-view />

    </v-app-bar>
</template>