<template>
  <div class="container">
    <h1 class="title">Welcome to our recipes website!</h1>
    <!-- <RecipePreviewList title="Randome Recipes" class="RandomRecipes center" /> -->
    <!-- <router-link v-if="!$root.store.username" to="/login" tag="button">You need to Login to view this</router-link> -->
    <div class="main_page">
    
    <div class="Random_Recipes">
      <div v-if = !$root.store.username>
        <!-- <RecipePreviewList
          title="Last Viewed Recipes"
          :class="{
            RandomRecipes: true,
            // blur: !$root.store.username,
            // center: true
            //''disabled'' after the }
          }"
        
                  
        ></RecipePreviewList> -->
        <RandomRecipe>

        </RandomRecipe>
        
        <!-- <div><img class=image-fit src="https://www.simplyrecipes.com/thmb/OCi18J2V8OeKDFV3FxoeKvgq74E=/1423x1067/smart/filters:no_upscale()/__opt__aboutcom__coeus__resources__content_migration__simply_recipes__uploads__2012__07__grilled-sweet-potatoes-horiz-a-1600-7c8292daa98e4020b447f0dc97a45cb7.jpg"></div>
        <div><img class=image-fit src="https://images.immediate.co.uk/production/volatile/sites/30/2020/08/chorizo-mozarella-gnocchi-bake-cropped-9ab73a3.jpg?quality=90&resize=556,505"></div>
        <div><img class=image-fit src="https://cdn.loveandlemons.com/wp-content/uploads/2020/03/pantry-recipes-2-500x500.jpg"></div> -->
        <!-- <img class=image-fit src="https://images.immediate.co.uk/production/volatile/sites/30/2020/08/chorizo-mozarella-gnocchi-bake-cropped-9ab73a3.jpg?quality=90&resize=556,505"> -->
      </div>

      <div v-else>
        Logged In
        
      </div>
    </div>

    <div class="Mainpage_login">
    <Login
      title="Login"
      :class="{
        
      }"
      disabled
    ></Login>
    </div>    

    </div>



    <!-- <div
      style="position: absolute;top: 70%;left: 50%;transform: translate(-50%, -50%);"
    >
      Centeredasdasdad
    </div> -->
  </div>
</template>

<script>
// import RecipePreviewList from "../components/RecipePreviewList";
import RandomRecipe from "../components/RandomRecipe";
import Login from "./LoginPage";
export default {
  mounted(){

  },
  components: {
    // RecipePreviewList,
    Login,
    RandomRecipe
  },
};
</script>

<style lang="scss" scoped>
.RandomRecipes {
  margin: 10px 0 10px;
}
.blur {
  -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
  filter: blur(2px);
}
::v-deep .blur .recipe-preview {
  pointer-events: none;
  cursor: default;
}

// .main_page{
//   //  text-align:center
   
// }

.Random_Recipes{
  // border:1px solid #000;
  display:inline-block;
  width: 50%;
  
}

.Mainpage_login{
  // border:1px solid red;
  display:inline-block;
  width: 50%;
  margin-top: 100px;
  vertical-align: top; /* here */

}
.image-fit{
  width: 300px; 
  height: 200px; 

  // object-fit: scale-down;
  object-fit:fill;


  // width: 300px; 
  // height: 337px; 
  // object-fit: contain;
}

</style>


