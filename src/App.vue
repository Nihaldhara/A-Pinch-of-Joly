<template>
  <div class="app">
    <header class="app-name">
      <h1>Recipes</h1>
    </header>
    <router-view></router-view>
    <footer class="footer"></footer>
  </div>
</template>

<style scoped>
.app {
  display: grid;
  height: 100dvh;
  width: 100dvh;
  grid-template-rows: 35% auto 15%;
  font-family: "Sansation", sans-serif;
  font-weight: 400;
  font-style: normal;
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
  font-size: 200px;
  color: darkorange;
  font-family: "Fascinate", system-ui;
  font-weight: 400;
  font-style: normal;
}

.footer {
  grid-area: footer;
}
</style>