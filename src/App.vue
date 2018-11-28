<template>
  <v-app>
    <v-container fluid px-0>
      <v-toolbar class="display-3"> Cart Buddy </v-toolbar>
        <v-list>
          <template v-for="(item, index) in items">
            <v-layout align-center >
              <v-checkbox  v-model="includeFiles" hide-details class="shrink mr-2"></v-checkbox>
              <v-autocomplete
                :items="grocery_database"
                :filter="customFilter"
                color="white"
                item-text="name"
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
        grocery_database: ["apples", "pears"],
        model: null,
        hasSaved: false,
      }
    },

    methods: {    
      onClick(){
        this.flaskdata = "hi mom";
      },
      addItem(){
        this.items.push(0);
      },
      customFilter (item, queryText, itemText) {
        const textOne = item.name.toLowerCase()
        const textTwo = item.abbr.toLowerCase()
        const searchText = queryText.toLowerCase()

        return textOne.indexOf(searchText) > -1 ||
          textTwo.indexOf(searchText) > -1
      },
      save() {
        this.isEditing = !this.isEditing
        this.hasSaved = true
      }
    },
  };
</script>

<style>

</style>
