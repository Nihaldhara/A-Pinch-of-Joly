<script>
import timer from '../assets/timer.svg'

export default {
  name: 'RecipeItem',

  components: {
    timer,
  },

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
      this.$emit('editRecipe', recipe)
    }
  },
}
</script>

<template>
  <div class="recipe">
    <div class="title">{{ recipe.title }}:</div>
    <div>Ingredients:</div>
    <ul class="ingredients">
      <li class="ingredient" v-for="ingredient in recipe.ingredients">{{ ingredient }}</li>
    </ul>
    <div>Time to make:</div>
    <div class="time-row">
      <timer class="icon"/>
      <div class="time">{{ recipe.time }}</div>
    </div>
    <div>Instructions:</div>
    <div class="instructions">{{ recipe.instructions }}</div>
    <div class="validation">
      <button class="edit" @click="editRecipe(recipe)">Edit</button>
      <button class="delete" @click="deleteRecipe(recipe)">Delete</button>
    </div>
  </div>
</template>

<style scoped>
.recipe {
  display: grid;
  background-color: #33312f;
  padding: 12px;
  border-radius: 12px;
}

.title {
  font-size: 24px;
  text-decoration: underline;
}

.ingredients {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(70px, 1fr));
  padding-left: 10px;
  grid-column-gap: 10px;
}

.ingredient {
  align-items: center;
  appearance: none;
  background-color: #515151;
  border-radius: 24px;
  border-style: solid;
  border-color: #3a3a3a;
  border-width: 2px;
  box-shadow: rgba(0, 0, 0, .2) 0 3px 5px -1px, rgba(0, 0, 0, .14) 0 6px 10px 0, rgba(0, 0, 0, .12) 0 1px 18px 0;
  box-sizing: border-box;
  color: rgba(246, 246, 246, 0.96);
  cursor: pointer;
  display: inline-flex;
  fill: currentcolor;
  font-size: 14px;
  font-weight: 500;
  height: 28px;
  justify-content: center;
  line-height: normal;
  max-width: 100%;
  overflow: visible;
  padding: 2px 24px;
  position: relative;
  text-align: center;
  text-transform: none;
  transition: box-shadow 280ms cubic-bezier(.4, 0, .2, 1), opacity 15ms linear 30ms, transform 270ms cubic-bezier(0, 0, .2, 1) 0ms;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  width: auto;
  will-change: transform, opacity;
  z-index: 0;
}

.ingredient:hover {
  background: #3a3a3a;
  color: rgba(246, 246, 246, 0.96);
}

.time-row {
  display: grid;
  grid-template-columns: 20px auto;
  grid-template-areas: "icon input";
  padding-left: 5px;
}

.icon {
  grid-area: icon;
}

.time {
  grid-area: input;
  padding-left: 10px;
}

.instructions {
  padding-left: 10px;
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