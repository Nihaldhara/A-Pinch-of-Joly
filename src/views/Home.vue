<script>

import RecipeForm from "@/components/RecipeForm.vue";
import RecipeItem from "@/components/RecipeItem.vue";

export default {
  name: 'Home',

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
  mounted() {
  },
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
      this.recipes.splice(index, 1)
    },
    editRecipe() {

    },
    viewRecipe(recipe) {

    }
  }
}

</script>

<template>
    <main class="main">
      <div class="create">
        <button v-if="!displayForm" @click="addRecipe">Add Recipe</button>
        <RecipeForm
            v-if="displayForm"
            @cancelCreate="cancelCreate"
            @saveRecipe="createRecipe"
        />
      </div>
      <ul class="recipes">
        <li v-for="recipe in recipes" :key="recipe.id">
          <RecipeItem
              :recipe="recipe"
              @editRecipe="editRecipe"
              @deleteRecipe="deleteRecipe"
          />
        </li>
      </ul>
    </main>

</template>

<style scoped>
.main {
  display: grid;
  grid-area: main;
  grid-template-areas:
    "create"
    "recipes";
}

.create {
  display: grid;
  grid-area: create;
}

.create button {
  height: 40px;
  width: 30%;
  justify-self: center;

}

.recipes {
  grid-area: recipes;
  margin: 0;
  padding: 0;
  list-style: none;
}
</style>
