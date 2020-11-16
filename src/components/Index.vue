<template>
    <v-app>
        <template>
            <div style="border-bottom: 1px solid lightgray">
                <v-app-bar
                color="white"
                flat
                app
                >
                <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
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
                        src="https://scontent.fmnl4-2.fna.fbcdn.net/v/t1.0-9/85221965_2668856169818185_7998544657929732096_o.jpg?_nc_cat=105&ccb=2&_nc_sid=09cbfe&_nc_eui2=AeE2aG4AH9FGMjNSuAy72r6jti0gOcBuDYa2LSA5wG4NhvB4hWUk64SfGWBxf395em1R33GJUPFfVceVcUWofsMK&_nc_ohc=35Ux5yVpzaEAX9wV7_I&_nc_ht=scontent.fmnl4-2.fna&oh=3c337a759c9e64941c0d4289b8e1a834&oe=5FD6F7CE"
                        alt="John"
                    >
                </v-avatar>

                </v-app-bar>
                
            </div>
            <v-navigation-drawer
                v-model="drawer"
                app
                >
                <v-list
                    nav
                    dense
                >
                    <v-list-item-group
                    v-model="group"
                    active-class="deep-purple--text text--accent-4"
                    >
                    <v-list-item>
                        <v-list-item-title>Foo</v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-title>Bar</v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-title>Fizz</v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-title>Buzz</v-list-item-title>
                    </v-list-item>
                    </v-list-item-group>
                </v-list>
            </v-navigation-drawer>
            <v-main app>
                    asd
            </v-main>
        </template>
    </v-app>
</template>

<script>
export default {
    data: () => ({
        drawer: true,
        group: null
    }),

    watch: {
        group(){
            this.drawer = false
        }
    }
}
</script>

<style scoped>
    div.v-toolbar__content{
        border-bottom: 1px solid lightgray;
    }
    div.v-toolbar__content{
        border-bottom: 1px solid black;
    }
</style>