<template>
  <div id="app">
    <!--<img alt="Vue logo" src="./assets/logo.png">
     <HelloWorld msg="Welcome to JooJar" />
    <span></span>
    <ButtonIcon @buttonText="popup"></ButtonIcon>
    <br>
    <ButtonIcon Icon="fa fa-users" Name="Users"></ButtonIcon> -->
    <navbar></navbar>

    <div class="container">
      <h5>Woooow</h5>
      <button class="btn btn-success" @click="isNew = !isNew">Create</button>
      <RecipeForm v-if="isNew" @saveRecipe="addRecepi"></RecipeForm>
      <input type="text" class="form-control" 
      v-model="searchtext">
      <ul>
        <li v-for="(recipe, index) in filterList" :key="index+recipe.title">
          {{ recipe.title }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import ButtonIcon from './components/ButtonIcon.vue'
import navbar from './Layout/navbar.vue'
import RecipeForm from './components/RecipeForm.vue'


export default {
  name: 'app',
  components: {
    navbar, RecipeForm
  },
  data () {
    return {
      recipes: [],
      isNew: false,
      searchtext: ''
    }
  },
  mounted () {
    if (localStorage.getItem('recipe')) {
      this.recipes = JSON.parse(localStorage.getItem('recipes'))
    }
  },
  computed: {
    filterList () {
      return this.recipes.filter(recipe => {
        return recipe.title.toLowerCase().indexof(this.searchtext.toLowerCase()) >-1
      })
    }
  },
  methods: {
    setLocalStorage () {
      localStorage.setItem('recipes', JSON.stringify(this.recipes))
    },
    addRecepi (recipe) {
      this.recipes.push(recipe)
      this.setLocalStorage()
      this.isNew = false
    },
    
  },
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
