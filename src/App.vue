<script>

import RecipeForm from "@/components/RecipeForm.vue";
import RecipeItem from "@/components/RecipeItem.vue";

export default {
  name: 'Pouic',

  components: {
    RecipeItem,
    RecipeForm,
  },

  data: () => ({
    recipes: JSON.parse(localStorage.getItem('recipeAppData')) || '[]',
    displayForm: false,
  }),
  watch: {
    recipes: {
      handler(recipes) {
        localStorage.setItem('recipeAppData', JSON.stringify(recipes))
      },
      deep: true
    }
  },
  mounted() {},
  computed: {},
  methods: {
    addRecipe() {
      this.displayForm = true
    },
    cancelCreate() {
      this.displayForm = false
    },
    createRecipe(recipe) {
      this.recipes.push(recipe)
      this.displayForm = false
    },
    deleteRecipe(recipe) {
      let index = this.recipes.indexOf(recipe)
      this.recipes.splice(index)
    },
    editRecipe() {

    }
  }
}

</script>

<template>
  <div class="app">
    <header class="app-name">
      <h1>Recipes</h1>
    </header>
    <main class="main">
      <button v-show="!displayForm" @click="addRecipe">Add Recipe</button>
      <RecipeForm
          v-show="displayForm"
          @cancelCreate="cancelCreate"
          @saveRecipe="createRecipe"
      />
      <ul>
        <li v-for="recipe in recipes" :key="recipe.id">
          <RecipeItem
              :recipe="recipe"
              @editRecipe="editRecipe"
              @deleteRecipe="deleteRecipe"
          />
        </li>
      </ul>
    </main>
    <footer class="footer"></footer>
  </div>
</template>

<style scoped>
.app {
  display: grid;
  min-height: 100dvh;
  min-width: 100dvh;
  grid-template-rows: 25% 60% 15%;
  grid-template-areas:
    "header"
    "main"
    "footer";
}

.app-name {
  grid-area: header;
}

.app-name h1 {
  text-align: center;
  font-size: 100px;
  color: darkorange;
}

.main {
  grid-area: main;
}

.footer {
  grid-area: footer;
}
</style>
