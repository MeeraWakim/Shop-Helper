<template>
  <v-app>
  <!--<div v-bind:style="{fontSize: '50px' }">-->
    <v-container fluid px-0>
      <v-toolbar class="display-3"> Cart Buddy </v-toolbar>
        <v-list>
          <template v-for="(item, index) in items">
            <v-layout align-center>
            <v-checkbox  v-model="includeFiles" hide-details class="shrink mr-2"></v-checkbox>
            
            <v-autocomplete
            
            

             v-model="model"
        :items="items"
        :loading="isLoading"
        :search-input.sync="search"
        color="white"
        hide-no-data
        hide-selected
        item-text="Description"
        item-value="API"
        label="Shopping list items"
        placeholder="Start typing to Search"
        prepend-icon="mdi-database-search"
        return-object

            ></v-autocomplete>
            
            </v-layout>   
          </template>
        </v-list>
        

      <v-icon large @click="addItem()">add_shopping_cart</v-icon>
      
    </v-container>
    
  </v-app>
</template>

<script>


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
          { 
            //header: 'Today' 
        
         descriptionLimit: 60,
      entries: [],
      isLoading: false,
      model: null,
      search: null
      },
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
     computed: {
      fields () {
        if (!this.model) return []

        return Object.keys(this.model).map(key => {
          return {
            key,
            value: this.model[key] || 'n/a'
          }
        })
      },
      items () {
        return this.entries.map(entry => {
          const Description = entry.Description.length > this.descriptionLimit
            ? entry.Description.slice(0, this.descriptionLimit) + '...'
            : entry.Description

          return Object.assign({}, entry, { Description })
        })
      }
    },

    watch: {
      search (val) {
        // Items have already been loaded
        if (this.items.length > 0) return

        // Items have already been requested
        if (this.isLoading) return

        this.isLoading = true

        // Lazily load input items
        axios.get('https://api.publicapis.org/entries')
          .then(res => {
            const { count, entries } = res.data
            this.count = count
            this.entries = entries
          })
          .catch(err => {
            console.log(err)
          })
          .finally(() => (this.isLoading = false))
      }
    }
  };
</script>

<style>

</style>
