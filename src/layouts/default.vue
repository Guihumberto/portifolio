<template>
  <v-app :theme="theme">
    <v-main>
      <headerApp @darkmode="changeTheme" />
      <router-view />
    </v-main>
    <AppFooter />
  </v-app>
</template>

<script setup>
  import headerApp from '@/layouts/headerApp.vue'

  const theme = ref('light')

  const changeTheme = (evento) => {
    if(evento.value) theme.value = 'dark'
    if(!evento.value) theme.value = 'light'
  }
  
</script>

<style>
*, *::before, *::after {
  box-sizing: border-box;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  text-decoration: none;
  border: none;
  outline: none;
  scroll-behavior: smooth;
  font-family: 'Poppins', sans-serif;
}
html{
  overflow-x: hidden;
  /* font-size: 62.5%; */
}
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}
#root, #__next {
  isolation: isolate;
}
</style>
