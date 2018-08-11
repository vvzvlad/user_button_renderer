<template>
   <v-container fluid>
      <v-layout row wrap>
         <v-flex xs12 class="py-2">
            <v-subheader class="pl-0">Air conditioner</v-subheader>
            <v-btn-toggle v-model="conditioner">
               <v-btn flat large block color="primary" value="off" @click="update('/airref/power/', 'OFF')">
                  Off conditioner
               </v-btn>
               <v-btn flat large block color="primary" value="on" @click="update('/airref/power/', 'ON')">
                  On conditioner
               </v-btn>
            </v-btn-toggle>
         </v-flex>
         <v-flex xs12 class="py-2">
            <v-divider></v-divider>
         </v-flex>
         <v-flex xs12 class="py-2">
            <v-subheader class="pl-0">Light(main room)</v-subheader>
            <v-btn-toggle v-model="main_light">
               <v-btn flat large block color="primary" value="off" @click="update('/dimmer/channel/1', '0')">
                  Off light
               </v-btn>
               <v-btn flat large block color="primary" value="on" @click="update('/dimmer/channel/1', '100')">
                  On light
               </v-btn>
            </v-btn-toggle>
         </v-flex>
         <v-flex xs12 class="py-2">
            <v-divider></v-divider>
         </v-flex>
         <v-flex xs12 class="py-2">
            <v-subheader class="pl-0">Light(other rooms)</v-subheader>
            <v-btn-toggle v-model="main_light">
               <v-btn flat large block color="primary" value="off" @click="update('/dimmer/channel/2', '0')">
                  Off light
               </v-btn>
               <v-btn flat large block color="primary" value="on" @click="update('/dimmer/channel/2', '100')">
                  On light
               </v-btn>
            </v-btn-toggle>
         </v-flex>

      </v-layout>
   </v-container>
</template>

<script>
import Vue from "vue";
import Axios from "axios";
import VueAxios from "vue-axios";
Vue.use(VueAxios, Axios);

export default {
  data() {
    return {
      text: "on",
      main_light: "on",
      conditioner: "on"
    };
  },
  methods: {
    update(topic, value) {
      Vue.axios
        .get("http://192.168.88.250:8080/system_bus", {
          params: {
            action: "update_value",
            value: value,
            topic: topic
          }
        })
        .then(response => {})
        .catch(error => {
          console.log(error);
          this.$refs.snackbar.update("Network error");
        });
    }
  }
};
</script>

<style scoped>
</style>
