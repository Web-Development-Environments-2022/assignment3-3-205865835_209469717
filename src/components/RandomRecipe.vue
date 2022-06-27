<template>
  <b-container>
    <div>
        <RecipePreview
        v-for="r in this.recipes" :key="r.id" 
        v-bind:id="r.id"
        v-bind:title="r.title"
        v-bind:readiInMinutes="r.readiInMinutes"
        v-bind:image="r.image"
        v-bind:aggregateLikes="r.aggregateLikes"
        v-bind:vegan="r.vegan"
        v-bind:vegetarian="r.vegetarian"
        v-bind:glutenFree="r.glutenFree"
        >

            
        </RecipePreview>
        <!-- <p>
           {{this.recipes}} 
        </p> -->
    </div>
  </b-container>
</template>

<script>
// import { axios } from 'vue/types/umd'
import RecipePreview from './RecipePreview';
    export default{
    name: "getRandomRecipe",
    components: {
        RecipePreview
    },
    
    data(){
        return{
            recipes: []        
        };
    },
    async mounted(){
        const response = await this.axios.get(
        "http://localhost:80/recipes/random"
        );
        this.recipes.push(response.data);

    }

}
</script>

<style>

</style>
