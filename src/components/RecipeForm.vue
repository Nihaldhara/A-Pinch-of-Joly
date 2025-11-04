<script>
export default {
  name: 'RecipeForm',

  props: [],

  emits: ['cancelCreate', 'saveRecipe'],

  data: () => ({
    id: '',
    title: '',
    ingredients: '',
    time: '',
    instructions: '',
  }),
  watch: {},
  mounted() {
  },
  computed: {},

  methods: {
    clearForm() {
      this.title=""
      this.ingredients=""
      this.time=""
      this.instructions=""
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
  }
}
</script>

<template>
  <div class="add-recipe">
    <input autofocus placeholder="Recipe Title" v-model="title">
    <input placeholder="Recipe Ingredients" v-model="ingredients">
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