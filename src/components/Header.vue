<template>
  <v-app-bar
    app
    color="primary"
    dark
  >
    <div class="d-flex align-center">
      <router-link to="/" class="title"><span>BOOK SEARCH</span></router-link>
    </div>
    <v-spacer></v-spacer>
    <v-btn to="/" text>HOME</v-btn>
  </v-app-bar>
</template>

<style scoped>
.title {
  cursor: pointer;
  text-decoration: none;
  color: white;
}
</style>