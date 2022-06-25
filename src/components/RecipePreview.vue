<template>
<div class ="all-details">
  <router-link
    @click.native="addToHistory"
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
        <div class="images">
          <img src="../assets/vegan.png" class="diet-image" v-if="typeof vegan === 'boolean' && vegan"/>
          <img src="../assets/vegetarian.png" class="diet-image" style="width: 22.5%; height: 22.5%;" v-if="typeof vegetarian === 'boolean' && vegetarian"/>
          <img src="../assets/gluten.png" class="diet-image" v-if="typeof glutenFree === 'boolean' && glutenFree"/>
        </div>
        <FavoriteHistory class="favorite-button" v-bind:id="this.id"/>
        <!-- <div v-if="$root.store.username">
          <div class="favorites" v-if="typeof favorite === 'boolean' && !favorite">
            <b-button @click="addToFavorites" variant="warning" >Save to favorites</b-button>          
          </div>        
          <div class="favorites" v-else>          
            <b-button variant="warning" disabled >Recipe saved to favorites</b-button>
          </div>
          <div class="watched" v-if="typeof watched === 'boolean' && !watched">
            <p class="recipe-details">You haven't viewed this recipe before</p>
          </div>        
          <div class="watched" v-else>          
            <p class="recipe-details">You viewed this recipe before</p>
          </div>
        </div>
        <div v-else>
            <div class="favorites">
             <b-button disabled style="filter: blur(1.3px); -webkit-filter: blur(1.3px);" variant="warning" src="../assets/saveFavorite.jpg">Save to favorites</b-button>          
            </div>              
            <div class="watched">          
              <p class="recipe-details">Login to save to favorites and see if viewed before</p>
            </div>
        </div> -->
      </ul>
    </div>
    <!-- <p class="recipe-details">{{ this.watched }} </p>
    <p class="recipe-details">{{ this.favorite }} </p> -->
</div>
  
</template>

<script>
import { PassThrough } from 'stream';
import FavoriteHistory from "../components/FavoriteHistory";


export default {
  components: {
    FavoriteHistory
  },
  async mounted() {
    this.axios.get(this.image, {withCredentials:false}).then((i) => {
      this.image_load = true;
    });
    this.history = await this.axios.get(
      "http://localhost:80/user/history",
      {
        params:{},
      }
    );
    this.favorites = await this.axios.get(
      "http://localhost:80/user/favorites",
      {
        params:{},
      }
    );
    let history_ids = [];
    for (let i = 0; i < this.history.data.length; i++) {
      history_ids.push(this.history.data[i].recipe_id);
    }
    let favorites_ids = [];
    for (let i = 0; i < this.favorites.data.length; i++) {
      favorites_ids.push(this.favorites.data[i].recipe_id);
    }
    this.favorite = favorites_ids.includes(this.id);
    this.watched = history_ids.includes(this.id);


  },
  data() {
    return {
      history : [],
      favorites : [],
      favorite : false,
      watched : false,
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
      type: Number,
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

    aggregateLikes: {
      type: Number,
      required: false,
      default() {
        return undefined;
      }
    }
  },
  methods:{
    async addToFavorites(){
      const response = await this.axios.post(
          "http://localhost:80/user/favorites" ,
          {
            recipe_id: this.id
          }
        );
    },
    async addToHistory(){
      const response = await this.axios.post(
          "http://localhost:80/user/history" ,
          {
            recipe_id: this.id
          }
        );
    }
  },
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
  margin-left: 10px;
  min-width: 100px;
  min-height: 100px;
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
  border-radius: 30px;
  background-position: left top;
  background-repeat: repeat;
  transition: transform .35s;
  border-collapse: inherit;
  
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

.images{
  min-height:50px;
}

.favorite-button{
  width: 205px;
}
</style>
