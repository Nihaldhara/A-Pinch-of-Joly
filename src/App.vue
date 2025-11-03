<script>

export default {
  name: 'Pouic',

  data: () => ({
    recipes: []
  }),
  watch: {},
  mounted() {
  },
  computed: {},
  methods: {
    addRecipe(event) {
      const value = event.target.value.trim();

      if (!value) {
        return;
      }

      this.recipes.push({
        id: Date.now(),
        title: value,
      });

      event.target.value = ''
    },
  }
}

</script>

<template>
  <div class="app">
    <header class="app-name">
      <h1>Recipes</h1>
    </header>
    <main class="main">
      <input autofocus class="new-todo" placeholder="New Recipe" @keyup.enter="addRecipe">
      <ul>
        <li v-for="recipe in recipes" :key="recipe.id">
          <div>{{recipe.title}}</div>
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
