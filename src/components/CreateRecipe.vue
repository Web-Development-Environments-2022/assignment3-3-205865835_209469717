<template>
    <div class="container">
    <h1 class="title-text">Create New Recipe</h1>



<div>
  <!-- Using modifiers -->
  <b-button v-b-modal.createRecipe>Create Recipe</b-button>

  <!-- Using value -->
  <!-- The modal -->
  <b-modal id="createRecipe" title="Create Your Own Recipe!">
    
    <b-form @submit.prevent="onSubmit">
    <!--Not onSubmit - on the method name. probably the one to register to db-->
      <b-form-group
        id="input-group-Recipe Name"
        label-cols-sm="3"
        label="RecipeName:"
        label-for="RecipeName"
      >
        <b-form-input
          class="inputs"
          id="RecipeName"
          
          type="text"
        ></b-form-input>
        <b-form-invalid-feedback>
          RecipeName is required  
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-ImageURL"
        label-cols-sm="3"
        label="ImageURL:"
        label-for="ImageURL"
      >
        <b-form-input
          class="inputs"
          id="ImageURL"
          type="URL"
        ></b-form-input>
        <b-form-invalid-feedback>
          ImageURL is required
        </b-form-invalid-feedback>
      </b-form-group>

            <b-form-group
        id="input-group-title Name"
        label-cols-sm="3"
        label="title:"
        label-for="title"
      >
      <b-form-input
          class="inputs"
          id="title"
          
          type="text"
        ></b-form-input>
        <b-form-invalid-feedback>
          title is required  
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-Total Time Name"
        label-cols-sm="3"
        label="TotalTime:"
        label-for="TotalTime"
      >
        <b-form-input
          class="inputs"
          id="TotalTime"
          
          type="text"
        ></b-form-input>
        <b-form-invalid-feedback>
          TotalTime is required  
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-Popularity"
        label-cols-sm="3"
        label="Popularity:"
        label-for="Popularity"
      >
        <b-form-input
          class="inputs"
          id="Popularity"
          
          type="text"
        ></b-form-input>
        <b-form-invalid-feedback>
          Popularity is required  
        </b-form-invalid-feedback>
      </b-form-group>

      <input type="checkbox" id="vegan" value="Vegan">
      <label for="vegan">Vegan</label>
      
      <input type="checkbox" id="gluten" value="Gluten">
      <label for="gluten">Gluten</label>


      
    </b-form>
  </b-modal>
</div>
    </div>  


</template>

<script>
import { BButton, BModal, VBModal } from "bootstrap-vue";


    export default {
      // name: CreateRecipe,
      components: {
          BButton,
          BModal
      },

      directives: { 
          'b-modal': VBModal 
      },
  }
</script>


<style>



</style>