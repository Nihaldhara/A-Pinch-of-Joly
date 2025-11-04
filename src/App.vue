<script>

import NewRecipe from "@/NewRecipe.vue";
import RecipeItems from "@/components/RecipeItems.vue";

export default {
  name: 'Pouic',

  components: {
    RecipeItems,
    NewRecipe,
  },

  data: () => ({
    recipes: [],
    displayForm: false,
  }),
  watch: {},
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
      <NewRecipe
          v-show="displayForm"
          @cancelCreate="cancelCreate"
          @saveRecipe="createRecipe"
      />
      <ul>
        <RecipeItems
          :recipes="recipes"
        />
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
