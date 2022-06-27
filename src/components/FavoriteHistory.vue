<template>
<div class ="all-details">
    <div v-if="$root.store.username">
        <div class="favorites" v-if="typeof favorite === 'boolean' && !favorite">
        <b-button class="favorite-button" @click="addToFavorites" variant="warning" >Save to favorites</b-button>          
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
    </div>
</div>
  
</template>

<script>

export default {
  async mounted() {
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
    }
  },
  methods:{
    async addToFavorites(){
      this.favorite = true;
      const response = await this.axios.post(
          "http://localhost:80/user/favorites" ,
          {
            recipe_id: this.id
          }
        );
    },
  },
};
</script>

<style scoped>


/* .favorite-button{
    width: 40%;
} */
.all-details{
  width: 25.7%;
  
}

.recipe-details{
  display: inline-block;
  margin-bottom: 5px;
  margin-top: 5px;
  font-family: 'Times New Roman', serif;
  /* font-size: large; */
  font-size:95%;
}

.favorites{
  margin-left: -25px;
}

.watched{
  display: inline-block;
  margin-left: -25px;
}


</style>
