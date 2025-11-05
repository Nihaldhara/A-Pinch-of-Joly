<script>
import timer from "@/assets/timer.svg";

export default {
  name: 'RecipeItem',

  components: {
    timer,
  },

  props: ['recipe'],

  emits: ['deleteRecipe', 'editRecipe'],

  data: () => ({
    editMode: false
  }),
  watch: {},
  mounted() {
  },
  computed: {},
  methods: {
    deleteRecipe(recipe) {
      this.$emit('deleteRecipe', recipe)
    },
    editRecipe(recipe) {
      this.toggleEditMode()
      this.$emit('editRecipe', recipe)
    },
    toggleEditMode() {
      this.editMode = !this.editMode
    }
  },
}
</script>

<template>

</template>

<style scoped>

.instructions {
  padding-left: 10px;
}

.validation {
  display: grid;
  grid-template-areas: "edit delete";
  margin-top: 10px;
}

.edit {
  grid-area: edit;
}

.delete {
  grid-area: delete;
}

</style>