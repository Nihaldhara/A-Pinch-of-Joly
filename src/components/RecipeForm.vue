<script>
export default {
  name: 'RecipeForm',

  props: [],

  emits: ['cancelCreate', 'saveRecipe'],

  data: () => ({
    id: '',
    title: '',
    ingredients: [],
    time: '',
    instructions: '',
  }),
  watch: {},
  mounted() {
  },
  computed: {},

  methods: {
    clearForm() {
      this.title = ""
      this.ingredients = []
      this.time = ""
      this.instructions = ""
    },
    cancelCreate() {
      this.clearForm()
      this.$emit('cancelCreate')
    },
    saveRecipe() {
      let recipe = {
        id: Date.now(),
        title: this.title,
        ingredients: this.ingredients,
        time: this.time,
        instructions: this.instructions,
      };

      this.clearForm()
      this.$emit('saveRecipe', recipe)
    },
    addIngredient(event) {
      const value = event.target.value.trim()

      if (!value) {
        return;
      }

      this.ingredients.push(value)
      event.target.value = ''
    }
  }
}
</script>

<template>
  <div class="add-recipe">
    <input autofocus placeholder="Recipe Title" v-model="title">
    <div class="ingredients">
      <input class="ingredient-input" placeholder="Recipe Ingredients" @keyup.enter="addIngredient">
      <div class="ingredients-list">
        <ul>
          <li class="ingredient" v-for="ingredient in ingredients">{{ ingredient }}</li>
        </ul>
      </div>
    </div>
    <input placeholder="Time to complete recipe" v-model="time">
    <input placeholder="Recipe Instructions" v-model="instructions">
    <div class="validation">
      <button class="save" @click="saveRecipe">Save</button>
      <button class="cancel" @click="cancelCreate">Cancel</button>
    </div>
  </div>
</template>

<style scoped>
.add-recipe {
  display: grid;
}

.ingredients {
  display: grid;
  grid-template-columns: 25% auto;
  grid-template-areas: "ingredient-input ingredients-list";
  align-content: center;
}

.ingredient-input {
  grid-area: ingredient-input;
}

.ingredients-list {
  grid-area: ingredients-list;
  align-content: center;
}

.ingredients-list ul {
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

.validation {
  display: grid;
  grid-template-areas:
    "save cancel";
}

.save {
  grid-area: save;
}

.cancel {
  grid-area: cancel;
}
</style>