<template>
<div class ="all-details">
  <router-link
    :to="{ name: 'recipe', params: { recipeId: id } }"
    class="recipe-preview">

    <div class="recipe-body">
      <img v-if="image_load" :src="image" class="recipe-image" />
    </div>
    </router-link>

    <div class="recipe-footer">
      <div :title="title" class="recipe-title">
        {{ title }}
      </div>
      <ul class="recipe-overview">
        <img src="../assets/clock.png" class="details-image" />
        <p class="recipe-details">{{ readyInMinutes }} minutes</p>     
        <br>
        <img src="../assets/like.png" class="details-image" />
        <p class="recipe-details">{{ aggregateLikes }} likes</p>
        <br>        
        <img src="../assets/vegan.png" class="diet-image" v-if="typeof vegan === 'boolean' && vegan"/>                
        <img src="../assets/vegetarian.png" class="diet-image" style="width: 22.5%; height: 22.5%;" v-if="typeof vegetarian === 'boolean' && vegetarian"/>
        <img src="../assets/gluten.png" class="diet-image" v-if="typeof glutenFree === 'boolean' && glutenFree"/>
        <div class="favorites" v-if="typeof favorite === 'boolean' && !favorite">
          <b-button variant="warning" src="../assets/saveFavorite.jpg">Save to favorites</b-button>          
        </div>        
        <div class="favorites" v-else>          
          <img src="../assets/favorite.png" class="details-image" />
          <p class="recipe-details">Recipe saved to favorites</p>
        </div>

        <div class="watched" v-if="typeof watched === 'boolean' && !watched">
          <p class="recipe-details">You haven't viewed this recipe</p>
        </div>        
        <div class="watched" v-else>          
          <p class="recipe-details">You viewed this recipe</p>
        </div>
        
      </ul>
    </div>
</div>
  
</template>

<script>
export default {
  mounted() {
    this.axios.get(this.image).then((i) => {
      this.image_load = true;
    });
  },
  data() {
    return {
      image_load: false,
    };
  },
  props: {
    id: {
      type: Number,
      required: true
    },
    title: {
      type: String,
      required: true
    },
    readyInMinutes: {
      type: String,
      required: true
    },
    image: {
      type: String,
      required: true
    },
    vegan: {
      type: Boolean,
      required: true
    },
    vegetarian: {
      type: Boolean,
      required: true
    },
    glutenFree: {
      type: Boolean,
      required: true
    },
    favorite: {
      type: Boolean,
      required: false,
      default() {
        return false;
      },
    },
    watched: {
      type: Boolean,
      required: false,
      default() {
        return false;
      },
    },
    aggregateLikes: {
      type: String,
      required: false,
      default() {
        return undefined;
      }
    }
  }
};
</script>

<style scoped>

.all-details{
  width: 25.7%;
}
.recipe-body {
  width: 20%;
  height: 20%;  
}

.recipe-footer .recipe-title{  
  font-size: x-large;
  font-family: Copperplate, Papyrus, fantasy;
  margin-left: 14px;
  
}

.recipe-details{
  display: inline-block;
  margin-bottom: 5px;
  margin-top: 5px;
  font-family: 'Times New Roman', serif;
  font-size: large;
}

.recipe-preview {  
  display: inline-block;
  width: 20%;
  height: 20%;
  position: relative;
  margin: 10px 10px;
}

.recipe-image{
  max-width: 2250%;
  height: auto;
  width: auto;
  border-radius: 15px;
  background-position: left top;
  background-repeat: repeat;
  transition: transform .35s;
}

.recipe-image:hover{
  transform: scale(1.05);
}

.details-image{
  width: 8.5%;
  height: 8.5%;
  margin-left: -15px;
  margin-right: 10px;
}

.diet-image{
  width: 17.5%;
  height: 17.5%;
  margin-left: -25px;
  margin-right: 60px;
}

.favorites{
  margin-left: -25px;
}

.watched{
  margin-left: -25px;
}
/*
.recipe-preview > .recipe-body {
  width: 100%;
  height: 200px;
  position: relative;
}

.recipe-preview .recipe-body .recipe-image {
  margin-left: auto;
  margin-right: auto;
  margin-top: auto;
  margin-bottom: auto;
  display: block;
  width: 98%;
  height: auto;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  background-size: cover;
}

.recipe-preview .recipe-footer {
  width: 100%;
  height: 50%;
  overflow: hidden;
}

.recipe-preview .recipe-footer .recipe-title {
  padding: 10px 10px;
  width: 100%;
  font-size: 12pt;
  text-align: left;
  white-space: nowrap;
  overflow: hidden;
  -o-text-overflow: ellipsis;
  text-overflow: ellipsis;
}

.recipe-preview .recipe-footer ul.recipe-overview {
  padding: 5px 10px;
  width: 100%;
  display: -webkit-box;
  display: -moz-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  -o-box-flex: 1;
  box-flex: 1;
  -webkit-flex: 1 auto;
  -ms-flex: 1 auto;
  flex: 1 auto;
  table-layout: fixed;
  margin-bottom: 0px;
}

.recipe-preview .recipe-footer ul.recipe-overview li {
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  -o-box-flex: 1;
  -ms-box-flex: 1;
  box-flex: 1;
  -webkit-flex-grow: 1;
  flex-grow: 1;
  width: 90px;
  display: table-cell;
  text-align: center;
} */
</style>
