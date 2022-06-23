<template>

  <div class="search-page">
    
    <b-form-group >
        <b-form-input class="search-field" placeholder="Search Recipes"></b-form-input>
        <b-input-group-append>
            <b-button type="submit" class="search-button"  variant="success"><img src="@/assets/search.png"></b-button>
        </b-input-group-append>
    </b-form-group>

    <h>Amount:</h>
    <b-form-select    
      v-model="amountSelected"
      :options="amountOptions"
      class="search-amount"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>

    <h>cuisine:</h>
    <b-form-select    
      v-model="cuisineSelected"
      :options="cuisineOptions"
      class="search-cuisine"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>
    
    <h>diet:</h>
    <b-form-select    
      v-model="dietSelected"
      :options="dietOptions"
      class="search-diet"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>
    
    <h>intolerance:</h>
    <b-form-select    
      v-model="intoleranceSelected"
      :options="intoleranceOptions"
      class="search-intolerance"
      value-field="item"
      text-field="name"
      disabled-field="notEnabled"
    ></b-form-select>
    
  </div>
  
</template>

<script>
  export default {
    data() {
      return {
        // query: '',
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
    }
  }
</script>

<style scoped>

.search-page{
  max-width: 500px;
  margin: auto;
}

.search-field {
  width: 70%;
  padding: 10px 35px 10px 15px;
  border-radius: 100px;
  outline: none;
  border: 3px solid #ccc;
  display: inline-block;
}

.search-button {
  
  background: transparent;
  border: none;
  outline: none;
  margin-left: -50px;
}


.search-button img {
  width: 20px;
  height: 20px;
  object-fit: cover;
}

.search-amount {
  display: inline-block;
  width: 10%;
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
  width: 20%;
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