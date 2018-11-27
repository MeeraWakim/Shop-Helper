<template>
  <v-app>

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
        flaskdata: 'HelloBitches',
      }
    },
    methods: {    onClick(){
      this.flaskdata = "hi mom";
    }
    },
    
};
</script>

<style>

</style>
