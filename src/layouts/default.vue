<template>
  <v-app :theme="theme">
    <headerApp @darkmode="changeTheme" />
    <v-main>
      <router-view />
    </v-main>
    <AppFooter />
  </v-app>
</template>

<script setup>
  import headerApp from '@/layouts/headerApp.vue'

  const theme = ref('dark')

  const changeTheme = (evento) => {
    if(evento.value) theme.value = 'dark'
    if(!evento.value) theme.value = 'light'
  }
  
</script>

<style>
 :root{
  --bg-color: rgb(20, 20, 20);
  --card-color: rgb(23, 23, 23);
  --primary-color: #f01468;
}
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
