<template>    
<section>
  <div class="container">
    <div class="text-center">
      <v-avatar size="8rem" color="dark">
        <v-icon size="7rem">mdi-account</v-icon>
      </v-avatar>
      <div class="my-2">
        <h1 class="text-h4 font-weight-bold">João Humberto</h1>
        <div class="text-body-2 font-weight-light m-n1 text-red">Desenvolvedor Frontend</div>
        <!-- <p class="text-body-2"> <v-icon size=".8rem" class="mr-1">mdi-email</v-icon>humberto.junior28@yahoo.com.br</p> -->
        <v-btn @click="whatsapp" variant="tonal"  prepend-icon="mdi-whatsapp">98 98465-0786</v-btn>
      </div>
    </div>
    <div class="cardsWrapper">
      <div id="cards">
        <div class="card" v-for="item, i in 1" :key="i">
          <div class="card-border"></div>
          <div class="card-content" :class="theme == 'dark' ? '': 'bg-white border'">
            <div class="wrappercontent">
              <div class="icon">
                <v-icon class="mb-1">mdi-account-tie</v-icon>
              </div>
              <div class="texto">
                <h3>Sobre</h3>
                <p class="font-weight-thin text-grey">Servidor Público há 13 anos, João Humberto Silva Ribeiro Júnior é desenvolvedor 
                  frontend nas horas vagas. Possui experência com desenvolvimento vue.js e nuxt.js, além de conhecimentos em html, css, javascript,
                  git, firebase, elasticsearch e outras frameworks e bibliotecas. <br>
                  Conheça alguns projetos públicados no portfólio abaixo.
                </p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="cardsWrapper">
      <h2>Portfólio</h2>
      <cards />
    </div>
    
  </div>
</section>
</template>

<script setup>
import { inject } from 'vue';

   const whatsapp = () =>{
    const telefone = '5598984650786';
    const mensagem = encodeURIComponent('Olá, gostaria de mais informações!');
    const url = `https://wa.me/${telefone}?text=${mensagem}`;
    
    window.open(url, '_blank');
   }

   const theme = inject('theme')
</script>

<style scoped>
section{
  width: min(100%, 1080px);
  margin-top: 10rem;
  margin-inline: auto;
  padding: 0 0.5rem;
}
.cardsWrapper{
  text-align: center;
  margin-bottom: 2rem;
}
.cardsWrapper h2{
  margin: 2rem 0;
}
#cards{
  width: min(100%, 916px);
  margin-inline: auto;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: .5rem;
}
#cards:hover > .card > .card-border {
  opacity: 1;
}
.card{
  background-color: rgba(255, 255, 255, 0.1);
  width: 910px;
  min-height: 160px;
  border-radius: 10px;
  position: relative;
  cursor: pointer;
}
.card::before,
.card > .card-border{
  border-radius: inherit;
  content: '';
  height: 100%;
  left: 0px;
  opacity: 0;
  transition: opacity 500ms;
  position: absolute;
  top: 0px;
  width: 100%;
}
.card::before{
  background: radial-gradient(
    800px circle at var(--mouse-x) var(--mouse-y),
    rgba(255, 255, 255, 0.06),
    transparent 40%
  );
  z-index: 3;
}
.card > .card-border{
  background: radial-gradient(
    400px circle at var(--mouse-x) var(--mouse-y),
    rgba(255, 255, 255, 0.3),
    transparent 40%
  );
  z-index: 1;
}
.card:hover::before
{
  opacity: 1;
}
.card > .card-content{
  background: var(--card-color);
  border-radius: inherit;
  margin: 1px;
  position: relative;
  height: calc(100% - 2px);
  width: calc(100% - 2px);
  z-index: 2;
}
.wrappercontent{
  margin: 0 1rem;
  display: flex;
  justify-content: left;
  align-items: baseline;
  gap: .8rem;
  line-height: 1.2;
  height: 30%;
}
.card-content .img{
  height: 70%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.texto{
  display: flex;
  flex-direction: column;
  align-items: first baseline;
  justify-content: flex-start;
  padding: 2rem 0.5rem;
}
.texto p {
  margin-top: 1rem;
  text-align: left;
  line-height: 1.4;
}
.container {
  animation: slideTop 2s ease;
  transition: .5s ease;
}
@keyframes slideTop {
  0%{
    opacity: 0;
    transform: translateY(100px);
  }
  100%{
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
