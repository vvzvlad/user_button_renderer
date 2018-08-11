<template>
   <v-container fluid>
      <v-layout row wrap>
         <v-flex xs12 class="py-2">
            <v-subheader class="pl-0">Sound</v-subheader>
            <v-btn-toggle v-model="text">
               <v-btn flat large block color="primary" value="off">
                  Off sound
               </v-btn>
               <v-btn flat large block color="primary" value="on">
                  On sound
               </v-btn>
            </v-btn-toggle>
         </v-flex>
         <v-flex xs12 class="py-2">
            <v-divider></v-divider>
         </v-flex>
         <v-flex xs12 class="py-2">
            <v-subheader class="pl-0">Volume</v-subheader>
            <v-slider v-model="slider"></v-slider>
         </v-flex>

      </v-layout>
   </v-container>
</template>

<script>
export default {
  data() {
    return {
      text: "on",
      slider: 10
    };
  }
};
</script>

<style scoped>
</style>
