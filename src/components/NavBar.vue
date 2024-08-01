<template>
    <v-app-bar flat>
        <template v-slot:prepend>
            <v-app-bar-nav-icon></v-app-bar-nav-icon>
        </template>
        <v-app-bar-title>Shopnow</v-app-bar-title>
        <v-spacer></v-spacer>
        <v-text-field density="compact" variant="solo" label="search products" append-inner-icon="mdi-magnify"
            single-line hide-details flat></v-text-field>
            <v-spacer></v-spacer>
            <v-btn prepend-icon="mdi mdi-download-circle-outline">
                <template v-slot:prepend>
                    <v-icon color="success"></v-icon>
                </template>
                DownloadApp
            </v-btn>
            <v-btn>Sign in/Login</v-btn>
        <router-view />

    </v-app-bar>
</template>