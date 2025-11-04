<script>
export default {
  name: 'RecipeItem',

  props: ['recipe'],

  emits: ['deleteRecipe', 'editRecipe'],

  data: () => ({}),
  watch: {},
  mounted() {
  },
  computed: {},
  methods: {
    deleteRecipe(recipe) {
      this.$emit('deleteRecipe', recipe)
    },
    editRecipe(recipe) {
      this.$emit('editRecipe')
    }
  },
}
</script>

<template>
  <div class="recipe">
    <div>{{ recipe.title }}</div>
    <div>{{ recipe.ingredients }}</div>
    <div>{{ recipe.time }}</div>
    <div>{{ recipe.instructions }}</div>
    <div class="validation">
      <button class="edit" @click="editRecipe(recipe)">Edit</button>
      <button class="delete" @click="deleteRecipe(recipe)">Delete</button>
    </div>
  </div>
</template>

<style scoped>
.recipe {
  display: grid;
}

.validation {
  display: grid;
  grid-template-areas: "edit delete";
}

.edit {
  grid-area: edit;
}

.delete {
  grid-area: delete;
}
</style>