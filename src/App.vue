<template>
  <v-app>
  <!--<div v-bind:style="{fontSize: '50px' }">-->
    <v-container fluid px-0>
      <v-toolbar class="display-3"> Cart Buddy </v-toolbar>
      <v-list>
        <template v-for="(item, index) in items">
     <v-layout align-center >
        <v-checkbox  v-model="includeFiles" hide-details class="shrink mr-2"></v-checkbox>
        <v-text-field class="display-4" height="200px"></v-text-field>
      </v-layout>     
        </template>
      </v-list>
      <v-icon large @click="addItem()">add_shopping_cart</v-icon>
      
    </v-container>
    
  </v-app>
</template>

<script>
import * as axios from 'axios';

export default {
    name: 'app',
    
    components: {
      
    },

    data() {
      return {
        checkbox: false,
        radioGroup: 1,
        switch1: true,
        flaskdata: 'HelloBitches',
        items: [
          { header: 'Today' },
          
        ],
      }
    },
    methods: {    onClick(){
      this.flaskdata = "hi mom";
    },
    addItem(){
      this.items.push(0);
    }
    },
    
};
</script>

<style>

</style>
