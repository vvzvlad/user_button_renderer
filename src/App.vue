<template>
   <v-app>
      <v-navigation-drawer persistent v-model="drawer" enable-resize-watcher fixed app>
         <v-list>
            <v-list-tile value="true" v-for="(item, i) in items" :key="i">
               <v-list-tile-action>
                  <v-icon v-html="item.icon"></v-icon>
               </v-list-tile-action>
               <v-list-tile-content>
                  <v-list-tile-title v-text="item.title"></v-list-tile-title>
               </v-list-tile-content>
            </v-list-tile>
         </v-list>
      </v-navigation-drawer>
      <v-toolbar app>
         <v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon>
         <v-toolbar-title v-text="title"></v-toolbar-title>
         <v-spacer></v-spacer>
      </v-toolbar>
      <v-content>
         <HelloWorld/>
      </v-content>
   </v-app>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld
  },
  data() {
    return {
      drawer: false,
      items: [
        {
          icon: "bubble_chart",
          title: "Inspire"
        },
        {
          icon: "bubble_chart",
          title: "Inspire"
        }
      ],
      title: "Glue user button"
    };
  }
};
</script>
