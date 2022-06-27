<template>
  <div class="container">


  <div class="text">
    <span>W</span>
    <span>E</span>
    <span>L</span>
    <span>C</span>
    <span>O</span>
    <span>M</span>
    <span>E</span>
    <span></span>
    <span>T</span>
    <span>O</span>
    <span></span>
    <span>O</span>
    <span>U</span>
    <span>R</span>
    <span></span>
    <span>R</span>
    <span>E</span>
    <span>C</span>
    <span>I</span>
    <span>P</span>
    <span>E</span>
    <span></span>
    <span>S</span>
    <span>I</span>
    <span>T</span>
    <span>E</span>
  </div>
    <div class="main_page">
    

    <div class="Mainpage_login">
    <Login/>
    </div>  

    <div class="Random_Recipes">
      <div v-if = !$root.store.username>
        <RandomRecipe/>
        
        
      </div>

      <div v-else>
        Logged In
        
      </div>
    </div>


    </div>


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
// .RandomRecipes {
//   margin-right: 500px;
// }
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
  width: 70%;
  height: 0%;
  vertical-align:top; /* here */
  margin-bottom: 100px;
}

.Mainpage_login{
  // border:1px solid red;
  display:inline-block;
  width: 30%;
  // margin-bottom: 100px;
  line-height: 100%;
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


.text {
  display: flex;
  justify-content: center;
  margin-top: 15vh;
  transform: translateY(-50%);
  // margin: 250px auto;
  text-align: center;
  // border: 1px solid #000;
  transition: transform .3s ease-in-out;
  font-size: 26px;
  
  &:hover {
    transform: rotateX(35deg), translateY(-50%);   
    span {
      color: #ccc;
      &:nth-child(odd) {
        transform: skewY(15deg);      
        // background-color: #f00;
        // box-shadow: 0 60px 20px rgba(0,0,0,0.1);
      }
      &:nth-child(even) {
        transform: skewY(-15deg);      
        background-color: #f9f9f9;
        color: #a6a6a6;
        // box-shadow: 0 60px 20px rgba(0,0,0,0.1);
      }
    }
  }
  
  > span {
    display: block;
    background-color: #fff;
    width: 120px;
    height: 120px;
    line-height: 120px;
    transition: transform .3s ease-in-out, color .3s ease-in-out, background-color .3s ease-in-out;
    box-shadow: 0 40px 50px rgba(0,0,0,0.1);
    &:first-child {
      border-radius: 5px 0 0 5px;
    }
  }
}

</style>


