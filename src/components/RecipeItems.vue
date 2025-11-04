<script>
export default {
  name: 'RecipeItems',

  props: ['recipes'],

  emits: [],

  data: () => ({}),
  watch: {},
  mounted() {
  },
  computed: {},
  methods: {},
}
</script>

<template>
  <li v-for="recipe in recipes" :key="recipe.id">
    <div class="recipe">
      <div>{{ recipe.title }}</div>
      <div>{{ recipe.ingredients }}</div>
      <div>{{ recipe.time }}</div>
      <div>{{ recipe.instructions }}</div>
    </div>
  </li>
</template>

<style scoped>

</style>