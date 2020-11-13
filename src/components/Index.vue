<template>
    <v-app>
        <template>
            <div style="border-bottom: 1px solid lightgray">
                <v-app-bar
                color="white"
                flat
                >
                <v-app-bar-nav-icon></v-app-bar-nav-icon>
                <v-app-bar-nav-icon class="ml-4"><v-icon size="40" color="yellow">mdi-google-keep</v-icon></v-app-bar-nav-icon>
               
                <v-toolbar-title class="ml-3 mr-5">Google Keep</v-toolbar-title>

                <v-spacer></v-spacer>

                <input type="text">

                <v-btn icon>
                    <v-icon>mdi-refresh</v-icon>
                </v-btn>

                <v-btn icon>
                    <v-icon>mdi-view-agenda-outline</v-icon>
                </v-btn>

                <v-btn icon>
                    <v-icon>mdi-cog</v-icon>
                </v-btn>

                <div class="mx-4"></div>

                <v-avatar size="40">
                    <img
                        src="https://cdn.vuetifyjs.com/images/john.jpg"
                        alt="John"
                    >
                </v-avatar>

                </v-app-bar>
            </div>
        </template>
    </v-app>
</template>



<style scoped>
    div.v-toolbar__content{
        border-bottom: 1px solid lightgray;
    }
    div.v-toolbar__content{
        border-bottom: 1px solid black;
    }
</style>