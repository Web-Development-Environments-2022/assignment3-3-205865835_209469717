<template>
    <div class="container">
<<<<<<< HEAD
    <!-- <h1 class="title-text">Create New Recipe</h1> -->



    <div>
  <!-- Using modifiers -->
<div class="w-30 ">
  <b-button text-decoration-none class="nav-link" variant="link" v-b-modal.createRecipe style="text-decoration: none;">Create Recipe</b-button>
</div>
  <!-- <a class="nav-link" href="" v-b-modal.createRecipe>Create Recipe</a> -->


  <!-- Using value -->
  <!-- The modal -->
  <b-modal 
    id="createRecipe" 
    ref="modal"
    title="Create Your Own Recipe!"
    @ok="handleOk"
    @show="resetModal"
    @hidden="resetModal"
    >
    
    <b-form @submit.prevent="onSubmit">
    <!--Not onSubmit - on the method name. probably the one to register to db-->
      <b-form-group
        id="input-group-Recipe Name"
        label="RecipeName:"
        label-for="title"
        :state="form.titleState"
      >
        <b-form-input required
          class="inputs"
          id="title"
          type="text"
          v-model="form.title"
          :state="form.titleState"
        ></b-form-input>
        <b-form-invalid-feedback>
          RecipeName is required  
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-ImageURL"
        label="Image URL:"
        label-for="ImageURL"
        :state="form.ImageURLState"
      >
        <b-form-input
          class="inputs"
          id="ImageURL"
          type="url"
          v-model="form.ImageURL"
          :state="form.ImageURLState"
        ></b-form-input>
        <b-form-invalid-feedback>
          ImageURL is required
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-TotalTime"
        label="Preperation Time:"
        label-for="TotalTime"
        :state="form.TotalTimeState"
      >
      <b-form-input
          class="inputs"
          id="TotalTime"
          type="number"
          v-model="form.TotalTime"
          :state="form.TotalTimeState"
        ></b-form-input>
        <b-form-invalid-feedback>
          Preperation Time is required  
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-Ingredients"
        label="Ingredients List and Amounts.
        (Use linebreak for each ingredients):"
        label-for="Ingredients"
        :state="form.IngredientsState"
      >
        <b-form-textarea
          class="inputs"
          id="Ingredients"
          v-model="form.Ingredients"
          :state="form.IngredientsState"
        ></b-form-textarea>
          <!-- <pre class="mt-3 mb-0">{{ Ingredients }}</pre> -->
        <b-form-invalid-feedback>
          Ingredients List and Amounts are required  
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-instructions"
        label="Instructions
        (Use linebreak for each stage):"
        label-for="instructions"
        :state="form.instructionsState"

      >
        <b-form-textarea
          class="inputs"
          id="instructions"
          v-model="form.instructions"
          :state="form.instructionsState"
        ></b-form-textarea>
        <b-form-invalid-feedback>
          Instructions is required 
        </b-form-invalid-feedback>
      </b-form-group>

      <b-form-group
        id="input-group-dishNum"
        label="Number of Dishes:"
        label-for="dishNum"
        :state="form.dishNumState"                  

      >
        <b-form-input
          class="inputs"
          id="dishNum"
          type="number"
          v-model="form.dishNum"
          :state="form.dishNumState"                  
        ></b-form-input>
        <b-form-invalid-feedback>
          Number of Dishes is required
        </b-form-invalid-feedback>
      </b-form-group>

      <input type="checkbox" v-model="form.vegan" id="vegan">
      <label for="vegan">  Vegan</label>
      <br>
      <input type="checkbox" v-model="form.vegetarian" id="vegetarian">
      <label for="vegetarian"> Vegetarian</label>
      <br>
      <input type="checkbox" id="glutenFree" v-model="form.glutenFree">
      <label for="glutenFree"> Gluten Free </label>


      
    </b-form>
  </b-modal>
=======

    <div>
  <div class="w-30 ">
    <b-button text-decoration-none class="nav-link" variant="link" v-b-modal.createRecipe style="text-decoration: none;">Create Recipe</b-button>
  </div>
    <b-modal 
      id="createRecipe" 
      ref="modal"
      title="Create Your Own Recipe!"
      @ok="handleOk"
      @show="resetModal"
      @hidden="resetModal"
      >
      
      <b-form @submit.prevent="onSubmit">
        <b-form-group
          id="input-group-Recipe Name"
          label="RecipeName:"
          label-for="title"
          :state="form.titleState"
        >
          <b-form-input required
            class="inputs"
            id="title"
            type="text"
            v-model="form.title"
            :state="form.titleState"
          ></b-form-input>
          <b-form-invalid-feedback>
            RecipeName is required  
          </b-form-invalid-feedback>
        </b-form-group>

        <b-form-group
          id="input-group-ImageURL"
          label="Image URL:"
          label-for="ImageURL"
          :state="form.ImageURLState"
        >
          <b-form-input
            class="inputs"
            id="ImageURL"
            type="url"
            v-model="form.ImageURL"
            :state="form.ImageURLState"
          ></b-form-input>
          <b-form-invalid-feedback>
            Please insert a valid URL
          </b-form-invalid-feedback>
        </b-form-group>

        <b-form-group
          id="input-group-TotalTime"
          label="Preperation Time:"
          label-for="TotalTime"
          :state="form.TotalTimeState"
        >
        <b-form-input
            class="inputs"
            id="TotalTime"
            type="number"
            v-model="form.TotalTime"
            :state="form.TotalTimeState"
          ></b-form-input>
          <b-form-invalid-feedback>
            Preperation Time is required  
          </b-form-invalid-feedback>
        </b-form-group>

        <b-form-group
          id="input-group-Ingredients"
          label="Ingredients List and Amounts.
          (Use linebreak for each ingredients):"
          label-for="Ingredients"
          :state="form.IngredientsState"
        >
          <b-form-textarea
            class="inputs"
            id="Ingredients"
            v-model="form.Ingredients"
            :state="form.IngredientsState"
          ></b-form-textarea>
          <b-form-invalid-feedback>
            Ingredients List and Amounts are required  
          </b-form-invalid-feedback>
        </b-form-group>

        <b-form-group
          id="input-group-instructions"
          label="Instructions
          (Use linebreak for each stage):"
          label-for="instructions"
          :state="form.instructionsState"

        >
          <b-form-textarea
            class="inputs"
            id="instructions"
            v-model="form.instructions"
            :state="form.instructionsState"
          ></b-form-textarea>
          <b-form-invalid-feedback>
            Instructions is required 
          </b-form-invalid-feedback>
        </b-form-group>

        <b-form-group
          id="input-group-dishNum"
          label="Number of Dishes:"
          label-for="dishNum"
          :state="form.dishNumState"                  

        >
          <b-form-input
            class="inputs"
            id="dishNum"
            type="number"
            v-model="form.dishNum"
            :state="form.dishNumState"                  
          ></b-form-input>
          <b-form-invalid-feedback>
            Number of Dishes is required
          </b-form-invalid-feedback>
        </b-form-group>

        <input type="checkbox" v-model="form.vegan" id="vegan">
        <label for="vegan">  Vegan</label>
        <br>
        <input type="checkbox" v-model="form.vegetarian" id="vegetarian">
        <label for="vegetarian"> Vegetarian</label>
        <br>
        <input type="checkbox" id="glutenFree" v-model="form.glutenFree">
        <label for="glutenFree"> Gluten Free </label>


        
      </b-form>
    </b-modal>
>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
</div>
    </div>  


</template>

<script>
import { BButton, BModal, VBModal } from "bootstrap-vue";
<<<<<<< HEAD
    export default {
      name: "CreateRecipe",
      components: {
          // BButton,
=======

    export default {
      name: "CreateRecipe",
      components: {
>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
          BModal
      },
      data(){
        return{
        form: {
        title: "",
        titleState: "" ,
        TotalTime: "",
        TotalTimeState: null ,
        ImageURL: "",
        ImageURLState: null ,
        Ingredients: "",
        IngredientsState: null ,
        instructions: "",
        instructionsState: null ,
        dishNum: "",
        dishNumState: null ,
        vegan:0,
        vegetarian: 0,
        glutenFree: 0
<<<<<<< HEAD
=======

>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
        },
        errors: [],
        validated: false
        }
      },
      
      methods:{
        handleOk(bvModalEvent) {
<<<<<<< HEAD
          // Prevent modal from closing
          bvModalEvent.preventDefault()
          // Trigger submit handler
          if (!this.checkFormValidity()) {
=======
          if (!this.checkFormValidity()) {
            bvModalEvent.preventDefault()
>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
            return
          }
          this.onSubmit()
        },      
<<<<<<< HEAD
        
        handleSubmit() {
          // Exit when the form isn't valid
          if (!this.checkFormValidity()) {
            return
          }
          // Push the name to submitted names
          // Hide the modal manually
          // this.$nextTick(() => {
          //   this.$bvModal.hide('modal-prevent-closing')
          // })
        },
=======

>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
        checkFormValidity() {
          if (this.form.title.length == 0){
            this.form.titleState = false
            return false
          }
          else 
            {
              this.form.titleState = true
            }
<<<<<<< HEAD
          if (this.form.ImageURL.length == 0){ //Might need to check if can verify valid URL.
            this.form.ImageURLState = false
            return false
            }
=======
          let url;
          try{
            url = new URL(this.form.ImageURL);
          }catch(error){
            this.form.ImageURLState = false 
            return false
          }
          if(url.protocol === "http:" || url.protocol === "https:"){
            if (this.form.ImageURL.length == 0){ 
              this.form.ImageURLState = false
              return false
              }
            else{
            this.form.ImageURLState = true
            }
          }
>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
          else{
            this.form.ImageURLState = true
          }
          if (this.form.TotalTime.length == 0 || this.form.TotalTime <= 0){
            this.form.TotalTimeState = false
            return false
            }
          else{
            this.form.TotalTimeState = true
          }
          if (this.form.Ingredients.length == 0){
            this.form.IngredientsState = false 
            return false
             }        
          else{
          this.form.IngredientsState = true
          }
          if (this.form.instructions.length == 0){
            this.form.instructions = false
            return false
            }
          else{
            this.form.instructionsState = true
          }
          if (this.form.dishNum.length == 0 || this.form.dishNum <= 0){
            this.form.dishNumState = false
            return false
            }
          else{
            this.form.dishNumState = true
          }
          
          if(this.form.vegan)
            this.form.vegan = 1
          else
            this.form.vegan = 0
          
          if(this.form.glutenFree)
            this.form.glutenFree = 1
          else
            this.form.glutenFree = 0
          
          if(this.form.vegetarian)
            this.form.vegetarian = 1
          else
            this.form.vegetarian = 0
<<<<<<< HEAD
=======

>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
          return true
        },
        resetModal() {
          this.form.title = "",
          this.form.titleState= null ,
          this.form.ImageURL= "",
          this.form.ImageURLState= null ,
          this.form.TotalTime= "",
          this.form.TotalTimeState= null ,
          this.form.Ingredients= "",
          this.form.IngredientsState= null ,
          this.form.instructions= "",
          this.form.instructionsState= null ,
          this.form.dishNum= "",
          this.form.dishNumState= null,
          this.form.vegan= 0,
          this.form.vegetarian = 0,
          this.form.glutenFree = 0
        },
        async onSubmit(){
          try{
           
<<<<<<< HEAD
            console.log(this.form.ImageURL)
            console.log(this.form.title)
            console.log(this.form.TotalTime)
            console.log(this.form.vegan)
            console.log(this.form.vegetarian)
            console.log(this.form.glutenFree)
            console.log(this.form.Ingredients)
            console.log(this.form.instructions)
            console.log(this.form.dishNum)
=======
>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
            const request = await this.axios.post(
            "http://localhost:80/user/createRecipe",       
            {
            title:this.form.title,
            imageUrl:this.form.ImageURL,
            totalTime:this.form.TotalTime,
            popularity:0,
            vegan:this.form.vegan,
            vegetarian:this.form.vegetarian,
            glutenFree:this.form.glutenFree,
            ingredients:this.form.Ingredients,
            instructions:this.form.instructions,
            servings:this.form.dishNum
          }
          )
          alert("recipe submitted successfuly!")
          this.resetModal()
<<<<<<< HEAD
          this.$refs[createRecipe].hide()
=======
>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
          }catch(err){
            alert("An error has accured, Please try again.")
          }
          
      },
<<<<<<< HEAD
      },
=======

      },

>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
      directives: { 
          'b-modal': VBModal 
      },
  }
      
</script>






<style>
<<<<<<< HEAD
=======

>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
label {
    /* Other styling... */
    /* text-align: right; */
    width:350px;
    white-space:normal;
}
<<<<<<< HEAD
=======

>>>>>>> b3e1664609069b635ee25f84daaaca13ac8c1363
</style>