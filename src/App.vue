<template>
  <v-app>
      <v-toolbar class="display-1"> Cart Buddy <v-card class="title">item count: {{price}} <br/> total price: ${{currentTotal}}</v-card></v-toolbar>
      <v-flex sm5 >
      <v-card>
        <v-list>
          <template v-for="(item, foodIndex) in itemsInList" v-bind:foodIndex="foodIndex" v-bind:price="price">
            <v-layout align-center>
              <v-checkbox v-model="checkBoxes[foodIndex]" hide-details class="shrink mr-2"></v-checkbox>
              <v-autocomplete
                :items="grocery_database"
                color="white"
                item-text="name" 
                v-model= "itemsInList[foodIndex]"
              ></v-autocomplete>
              <v-btn @click="submitItem()" color="success">Submit</v-btn>
              <v-btn flat @click="clearItem(foodIndex)"><v-icon>clear</v-icon></v-btn>
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
        
        currentStrg: '',
        currentRmvStrg: '',
        price:1,
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
          'Apples',
          'Asparagus',
          'Avocado',
          'Bacon',
          'Bananas',
          'Beef, Ground',
          'Beer, Shiner Bock',
          'Bread',
          'Cheerios',
          'Provolone Cheese',
          'Cheez-its',
          'Chicken Breast',
          'Coffee',
          'Dr Pepper',
          'Eggs',
          'Garlic',
          'Grapes',
          'Honey',
          'Jello',  
          'Ketchup',
          'Mandarins',
          'Mayonaise',
          'Milk',
          'Rice',
          'Spaghetti',
          'Spaghetti Sauce',
          'Strawberries',
          'Soup',
          'Turkey',
          'Yogurt'],

        currentTotal: 0,
        model: null,
        hasSaved: false,
        priceindex: 0,
        priceRemoveIndex: 0,
        price_database:[
         1,
         2,
         2,
         5.50,
         0.50,
         4,
         8,
         2.50,
         3,
         3,
         3,
         4,
         5,
         3,
         2,
         1.50,
         2,
         4,
         1 ,  
         3,
         5,
         3,
         3.50,
         1,
         1.50,
         2,
         3,
         1,
         3,
         1],  

        itemsInList: [{}],
        checkBoxes: [{}],
      }
    },

    methods: {  
      submitItem(){
        for (var i = 0; i < this.itemsInList.length; i++) {
          this.currentStrg = String(this.itemsInList[i]);
          console.log("current string: " + this.currentStrg);
          for (var q = 0; q < this.grocery_database.length; q++){
            if (this.currentStrg === String(this.grocery_database[q])) {
              
              this.priceindex = q;
              this.currentTotal += this.price_database[this.priceindex];
            }
          
          console.log( "price database item: " + String(this.price_database[this.price.index]));
          }
        }

        //console.log(this.priceIndex);
        console.log("current total: " + this.currentTotal);
        //console.log("price:" + this.price_database[this.priceindex]);
        
      }, 
      addItem(){
        this.itemsInList.push(0);
        this.checkBoxes.push(0);
        this.price = this.itemsInList.length;

        
        } , 
      

      clearItem(foodIndex){
        this.itemsInList.splice(foodIndex,1);
        console.log("items in list: "+this.itemsInList);
        this.price = this.itemsInList.length;
        

        for (var i = 0; i < this.itemsInList.length; i++) {
          this.currentRmvStrg = String(this.itemsInList[i]);
          console.log("current remove string: " + this.currentRmvStrg);
          for (var q = 0; q < this.grocery_database.length; q++){
            if (this.currentRmvStrg === String(this.grocery_database[q])) {
              
              this.priceRemoveIndex = q;
              this.currentTotal -= this.price_database[this.priceRemoveIndex];
            }
            //console.log( "grocery database item: " + String(this.grocery_database[q]));
          }
        }
        
      },


      // autocompleteAdded(){
      //   console.log("I just triggered autocomplete");
        // console.log(this.price);
      // },
    },
  };
</script>

<style>

</style>
