<template>
    <v-app>
        <v-app-bar app color="white" elevate-on-scroll>
            <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
            <v-app-bar-nav-icon class="ml-4"><v-icon size="40" color="yellow">mdi-google-keep</v-icon></v-app-bar-nav-icon>
        
            <v-toolbar-title class="ml-3 mr-5">Google Keep</v-toolbar-title>

            <v-spacer></v-spacer>

            <v-card class="input-wrapper d-none d-sm-flex" width="374">
                <input v-model="search" type="text" class="search" placeholder="Search . . .">
            </v-card>

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
        </v-app-bar >
        <v-navigation-drawer v-model="drawer" app>
           <v-list
                nav
                dense
            >
                <v-list-item-group
                >
                <v-list-item>
                    <v-list-item-title>
                        <span><v-icon>mdi-lightbulb-outline</v-icon></span>
                        <span class="ml-5"></span>
                        <span class="col align-items-center">Notes</span>
                    </v-list-item-title>
                </v-list-item>

                <v-list-item>
                    <v-list-item-title>
                        <span><v-icon>mdi-bell-outline</v-icon></span>
                        <span class="ml-5"></span>
                        <span class="col align-items-center">Reminders</span>
                    </v-list-item-title>
                </v-list-item>

                <v-list-item>
                    <v-list-item-title>
                        <span><v-icon>mdi-pencil-outline</v-icon></span>
                        <span class="ml-5"></span>
                        <span class="col align-items-center">Edit Label</span>
                    </v-list-item-title>
                </v-list-item>

                <v-list-item>
                    <v-list-item-title><span><v-icon>mdi-archive-outline</v-icon></span>
                    <span class="ml-5"></span>
                    <span class="col align-items-center">Archive</span></v-list-item-title>
                </v-list-item>
                
                <v-list-item>
                    <v-list-item-title>
                        <span><v-icon>mdi-trash-can-outline</v-icon></span>
                        <span class="ml-5"></span>
                        <span class="col align-items-center">Trash</span>
                    </v-list-item-title>
                </v-list-item>
                </v-list-item-group>
            </v-list>
        </v-navigation-drawer>
        <div class="content-wrapper">
            <!-- <vue-masonry-wall :items="resultQuery" :options="{width: 300, padding: 7}" >
                    <template v-slot:default="{item}">
                            <div class="item px-4 py-3" :class="{ 'selected' : item.selected == true}">
                                <div class="float-right">
                                    <v-icon small @click="selectNote(item)" v-if="item.selected == false">mdi-circle-outline</v-icon>
                                    <v-icon small @click="selectNote(item)" v-else color="blue">mdi-check-circle</v-icon>
                                </div>
                                <h5>{{item.title}}</h5>
                                <p>{{item.content}}</p>
                            </div>
                    </template>
            </vue-masonry-wall> -->
            <masonry
            :cols="4"
            :gutter="30"
            >
            <div v-for="(item, index) in resultQuery" :key="index">
                <div class="item px-4 py-3 my-3" :class="{ 'selected' : item.selected == true}">
                    <div class="float-right">
                        <v-icon small @click="selectNote(item)" v-if="item.selected == false">mdi-circle-outline</v-icon>
                        <v-icon small @click="selectNote(item)" v-else color="blue">mdi-check-circle</v-icon>
                    </div>
                    <h5>{{item.title}}</h5>
                    <p>{{item.content}}</p>
                </div>
            </div>
            </masonry>
            <div class="floating" v-show="selectionActive == true">
                <v-btn
                    color="red"
                    dark
                    fab
                >
                    <v-icon>mdi-trash-can-outline</v-icon>
                </v-btn>
            </div>
        </div>
        
    </v-app>
</template>

<script>
// import VueMasonryWall from "vue-masonry-wall";
// import VueMasonry from 'vue-masonry-css'
export default {
    // components: {VueMasonry},
    data: () => ({
        drawer: true,
        mini: true,
        selectionActive: false,
        search: null,
        items: [
          {title: 'Item 0', content: 'hey1', selected: false},
          {title: 'Item 1', content: 'quam sed ex sagittis tempus.', selected: false},
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.', selected: false},
          {title: 'Item 1', content: 'Donec maximus leo quis leo pharetra sodales. Cras suscipit quam sed ex sagittis tempus.', selected: false},
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.', selected: false},
          {title: 'Item 0', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit.', selected: false},

        ]
    }),

    methods: {
        selectNote(item) {
            item.selected = !item.selected
            const isThereSelected = Object.values(this.items).filter(items => items.selected == true);

            if(isThereSelected.length == 0){
                this.selectionActive = false   
            }
            else{
                this.selectionActive = true
            }
        }
    },

    computed: {
        resultQuery(){
            if(this.search){
                return this.items.filter((item) => {
                    return this.search.toLowerCase().split(' ').every(v => item.title.toLowerCase().includes(v))
                })
            }
            else{
                return this.items
            }
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

    .item{
        border: 1px solid lightgray;
        border-radius: 10px;
        display: float;
    }

    .content-wrapper{
        margin: 20px 100px;
    }

    .search{
        background: white;
        width: 100%;
    }

    .search:focus{
        outline: none;
    }

    .input-wrapper{
        padding: 8px 10px;
    }

    .selected{
        border: 1px solid dodgerblue;
        transition: 0.5s;
    }

    .floating{
        position: fixed;
        bottom: 30px;
        right: 30px;
        z-index: 99;
        transition: 0.4s;
    }
</style>