<template>
  <div class="container">

    
    <h1 class="title">Search Page</h1>
    <!-- <SearchBar title="searchBar" class="search-bar" />     -->
    <b-form-group >
        <b-form-input v-on:keyup.enter="search"  v-model="searchQuery" class="search-field" placeholder="Search Recipes" ></b-form-input>
        <!-- <b-button type="submit" class="search-button"  variant="success"> search<img src="@/assets/search.png"></b-button> -->
        <img img src="@/assets/search.png" class="search-image">
    </b-form-group>

    <b>Amount:</b>
    <b-form-select    
      v-model="amountSelected"
      :options="amountOptions"
      class="search-amount"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>

    <b>cuisine:</b>
    <b-form-select    
      v-model="cuisineSelected"
      :options="cuisineOptions"
      class="search-cuisine"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>
    
    <b>diet:</b>
    <b-form-select    
      v-model="dietSelected"
      :options="dietOptions"
      class="search-diet"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>
    
    <b>intolerance:</b>
    <b-form-select    
      v-model="intoleranceSelected"
      :options="intoleranceOptions"
      class="search-intolerance"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>
    
    <div>
        <RecipePreview class="recipePreview" v-bind:id="635350" title="Blue Cheese Burgers" readyInMinutes=45 image="https://spoonacular.com/recipeImages/635350-312x231.jpg" aggregateLikes=7 v-bind:vegan="true" v-bind:vegetarian="true" v-bind:glutenFree="true"/>      
        <RecipePreview class="recipePreview" v-bind:id="635350" title="Blue Cheese Burgers" readyInMinutes=45 image="https://spoonacular.com/recipeImages/635350-312x231.jpg" aggregateLikes=7 v-bind:vegan="true" v-bind:vegetarian="true" v-bind:glutenFree="true"/>      
        <RecipePreview class="recipePreview" v-bind:id="635350" title="Blue Cheese Burgers" readyInMinutes=45 image="https://spoonacular.com/recipeImages/635350-312x231.jpg" aggregateLikes=7 v-bind:vegan="true" v-bind:vegetarian="true" v-bind:glutenFree="true"/>      
        <RecipePreview class="recipePreview" v-bind:id="635350" title="Blue Cheese Burgers" readyInMinutes=45 image="https://spoonacular.com/recipeImages/635350-312x231.jpg" aggregateLikes=7 v-bind:vegan="true" v-bind:vegetarian="true" v-bind:glutenFree="true"/>      
        <RecipePreview class="recipePreview" v-bind:id="635350" title="Blue Cheese Burgers" readyInMinutes=45 image="https://spoonacular.com/recipeImages/635350-312x231.jpg" aggregateLikes=7 v-bind:vegan="true" v-bind:vegetarian="true" v-bind:glutenFree="true"/>      
    </div>
    
  </div>


</template>

<script>
// import SearchBar from "../components/SearchBar";
// export default {
//   components: {
//     SearchBar
//   }
import { METHODS } from 'http'


import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

// };
import RecipePreviewList from "../components/RecipePreviewList";
import RecipePreview from "../components/RecipePreview";

export default {
  name: "SearchPage",
  components: {
    // RecipePreviewList
    RecipePreview
  },
  data() {
    return {
      searchQuery: '',
      amountSelected: '5',
      amountOptions: [
        { item: '5', name: '5' },
        { item: '10', name: '10' },          
        { item: '15', name: '15' }
      ],
      cuisineSelected: 'All Cuisines',
      cuisineOptions: [
        { item: 'All Cuisines', name: 'All Cuisines' },
        { item: 'African', name: 'African' },
        { item: 'American', name: 'American' },          
        { item: 'British', name: 'British' },
        { item: 'Cajun', name: 'Cajun' },
        { item: 'Caribbean', name: 'Caribbean' },          
        { item: 'Chinese', name: 'Chinese' },
        { item: 'Eastern European', name: 'Eastern European' },
        { item: 'European', name: 'European' },          
        { item: 'French', name: 'French' },
        { item: 'German', name: 'German' },
        { item: 'Greek', name: 'Greek' },          
        { item: 'Indian', name: 'Indian' },
        { item: 'Italian', name: 'Italian' },
        { item: 'Japanese', name: 'Japanese' },          
        { item: 'Jewish', name: 'Jewish' },
        { item: 'Korean', name: 'Korean' },
        { item: 'Latin American', name: 'Latin American' },          
        { item: 'Mediterranean', name: 'Mediterranean' },
        { item: 'Mexican', name: 'Mexican' },
        { item: 'Middle Eastern', name: 'Middle Eastern' },          
        { item: 'Nordic', name: 'Nordic' },
        { item: 'Southern', name: 'Southern' },
        { item: 'Spanish', name: 'Spanish' },          
        { item: 'Thai', name: 'Thai' },
        { item: 'Vietnamese', name: 'Vietnamese' }
      ],
      dietSelected: 'All Diets',
      dietOptions: [
        { item: 'All Diets', name: 'All Diets' },
        { item: 'Gluten Free', name: 'Gluten Free' },
        { item: 'Ketogenic', name: 'Ketogenic' },
        { item: 'Vegetarian', name: 'Vegetarian' },
        { item: 'Lacto-Vegetarian', name: 'Lacto-Vegetarian' },
        { item: 'Ovo-Vegetarian', name: 'Ovo-Vegetarian' },
        { item: 'Vegan', name: 'Vegan' },
        { item: 'Pescetarian', name: 'Pescetarian' },
        { item: 'Paleo', name: 'Paleo' },
        { item: 'Primal', name: 'Primal' },
        { item: 'Low FODMAP', name: 'Low FODMAP' },
        { item: 'Whole30', name: 'Whole30' }          
      ],
      intoleranceSelected: 'No Intolerances',
      intoleranceOptions: [
        { item: 'No Intolerances', name: 'No Intolerances' },
        { item: 'Dairy', name: 'Dairy' },
        { item: 'Egg', name: 'Egg' },       
        { item: 'Gluten', name: 'Gluten' },
        { item: 'Grain', name: 'Grain' },     
        { item: 'Peanut', name: 'Peanut' },
        { item: 'Seafood', name: 'Seafood' },       
        { item: 'Seasame', name: 'Seasame' },
        { item: 'Shellfish', name: 'Shellfish' },  
        { item: 'Soy', name: 'Soy' },
        { item: 'Sulfite', name: 'Sulfite' },       
        { item: 'Tree Nut', name: 'Tree Nut' },
        { item: 'Wheat', name: 'Wheat' }          
      ]
    }
  },
  // mounted(){
  //   this.search();
  // },
  methods:{
    async search(){
      var that = this;
      var cuisine_ = ' ';
      if (that.cuisineSelected != "All Cuisines"){
        cuisine_ = that.cuisineSelected;
      }
      var diet_ = ' ';
      if (that.dietSelected != "All Diets"){
        diet_ = that.dietSelected;
      }
      var intolerance_ = ' ';
      if (that.intoleranceSelected != "No Intolerances"){
        intolerance_ = that.intoleranceSelected;
      }
      try{
        const response = await this.axios.get(
          "http://localhost:80/recipes/search" + "/" + that.searchQuery + "/" + that.amountSelected,
          {
            params:{
              cuisine: cuisine_,
              diet: diet_,
              intolerance: intolerance_,
            },
          }
        );
        const recipes = response.data;
        this.recipes = [];
        this.recipes.push(...recipes);
        console.log(response);
      }
      catch(error){
        console.log(error);
      } 
    }
  }
}
</script>


<style>

.recipePreview{
  display: inline-block;
  margin-right: 50px;
}
.search-field {
  width: 70%;
  padding: 10px 35px 10px 15px;
  border-radius: 100px;
  outline: none;
  border: 3px solid #ccc;
  display: inline-block;
}

/* .search-button {
  
  background: transparent;
  border: none;
  outline: none;
  margin-left: -50px;
} */


.search-image {
  width: 20px;
  height: 20px;
  margin-left: -50px;
  object-fit: cover;
}

.search-amount {
  display: inline-block;
  width: 5%;
  height: 100%;
  position: relative;  
  border-radius: 15px;
  white-space: pre;
  margin-top: 2px;
  margin-bottom: 10px;
  margin-right: 10px;
  margin-left: 10px;
  
}
.search-cuisine, .search-diet, .search-intolerance{
  display: inline-block;
  width: 13%;
  height: 100%;
  position: relative;  
  border-radius: 15px;
  white-space: pre;
  margin-top: 2px;
  margin-bottom: 10px;
  margin-right: 10px;
  margin-left: 10px;
}
</style>