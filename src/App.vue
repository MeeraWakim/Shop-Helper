<template>
  <v-app>
    
      <v-toolbar class="display-2"> Cart Buddy </v-toolbar>
      <v-flex  sm5 >
      <v-card>
        <v-list>
          <template v-for="(item, index) in itemsInList" v-bind:index="index">
            <v-layout align-center>
              <v-checkbox v-model="checkBoxes[index]" hide-details class="shrink mr-2"></v-checkbox>
              <v-autocomplete
                :items="grocery_database"
                :filter="customFilter"
                color="white"
                item-text="name"
                v-model= "itemsInList[index]"
              ></v-autocomplete>
              <v-btn flat @click="clearItem(index)"><v-icon>clear</v-icon></v-btn>
            </v-layout>
          </template>
        </v-list>
        
      <v-icon align-left large @click="addItem()">add_shopping_cart</v-icon>
      </v-card>
      </v-flex>
  </v-app>
</template>

<script>
export default {
    name: 'app',
    
    components: {
      
    },

    data() {
      return {
        grocery: '',
        checkbox: false,
        radioGroup: 1,
        switch1: true,
        descriptionLimit: 60,
        entries: [],
        isLoading: false,
        model: null,
        search: null,
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
          { name: 'Yogurt', price: '1'} ],
        model: null,
        hasSaved: false,
        itemsInList: [{}],
        chosenItem: [{}],
        checkBoxes: [{}],
      }
    },

    methods: {    
      onClick(){
        this.flaskdata = "hi mom";
      },
      addItem(){
        this.itemsInList.push(0);
        this.chosenItem.push(0);
        console.log(this.itemsInList);
      },
      clearItem(index){
        this.itemsInList.splice(index,1);
        console.log(this.itemsInList);
      },
      autocompleteAdded(){
        console.log("autocomplete triggered");
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
      },
    },
  

  };
</script>

<style>

</style>
