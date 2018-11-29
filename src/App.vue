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
        grocery_database: [
          { name: 'Apples', price: '1'},
          { name: 'Asparagus', price: '2'},
          { name: 'Avacados', price: '2'},
          { name: 'Bacon', price: '5.5'},
          { name: 'Bananas', price: '0.5'},
          { name: 'Beef, Ground', price: '4'},
          { name: 'Beer, Shiner Bock', price: '8'},
          { name: 'Bread', price: '2.5'},
          { name: 'Cheerios', price: '3'},
          { name: 'Provolone Cheese', price: '3'},
          { name: 'Cheez-its', price: '3'},
          { name: 'Chicken Breast', price: '4'},
          { name: 'Coffee', price: '5'},
          { name: 'Dr Pepper', price: '3'},
          { name: 'Eggs', price: '2'},
          { name: 'Garlic', price: '1.5'},
          { name: 'Grapes', price: '2'},
          { name: 'Honey', price: '4'},
          { name: 'Jello', price: '1'} ,  
          { name: 'Ketchup', price: '3'},
          { name: 'Mandarins', price: '5'},
          { name: 'Mayonaise', price: '3'},
          { name: 'Milk', price: '3.5'},
          { name: 'Rice', price: '1'},
          { name: 'Spaghetti', price: '1.5'},
          { name: 'Spaghetti Sauce', price: '2'},
          { name: 'Strawberries', price: '3'},
          { name: 'Soup', price: '1'},
          { name: 'Turkey', price: '3'},
          { name: 'Yogurt', price: '1'}
       

          ],
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
        const textTwo = item.price.toLowerCase()
        const searchText = queryText.toLowerCase()

        return textOne.indexOf(searchText) > -1 ||
          textTwo.indexOf(searchText) > -1
      },
      save() {
        this.isEditing = !this.isEditing
        this.hasSaved = true
      }
    },
  
var sum = array.reduce(function(pv, cv) { return pv + cv; }, 0);

  };
</script>

<style>

</style>
