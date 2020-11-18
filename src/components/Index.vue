<template>
    <v-app>
        <v-app-bar app flat>
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
        <v-navigation-drawer app>
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

        
        <div class="content-wrapper">
            <vue-masonry-wall :items="items" :options="{width: 300, padding: 10}" @append="append">
                <template v-slot:default="{item}">
                    <div class="item px-4 py-3">
                        <h5>{{item.title}}</h5>
                        <p>{{item.content}}</p>
                    </div>
                </template>
            </vue-masonry-wall>
        </div>
    </v-app>
</template>

<script>
import VueMasonryWall from "vue-masonry-wall";
export default {
    components: {VueMasonryWall},
    data: () => ({
        drawer: true,
        items: [
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.'},
          {title: 'Item 1', content: 'Donec maximus leo quis leo pharetra sodales. Cras suscipit quam sed ex sagittis tempus. leo quis leo pharetra sodales. Cras suscipit quam sed ex sagittis tempus.'},
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.'},
          {title: 'Item 1', content: 'Donec maximus leo quis leo pharetra sodales. Cras suscipit quam sed ex sagittis tempus.'},
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.'},
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.'},

        ]
    }),
}
</script>

<style scoped>

    div.v-toolbar__content{
        border-bottom: 1px solid lightgray;
    }

    div.v-toolbar__content{
        border-bottom: 1px solid black;
    }

    .item{
        border: 1px solid lightgray;
        border-radius: 10px;
    }

    .content-wrapper{
        margin: 20px 50px;
    }
</style>