<template>
     <div id="cards">
      <div class="card" v-for="item, i in list" :key="i" @click="goTo(item.url)">
        <div class="card-border"></div>
        <div class="card-content" :class="theme == 'dark' ? '': 'bg-white border'">
          <div class="img">
            <v-icon color="grey" size="80">{{item.icon}}</v-icon>
          </div>
          <div class="wrappercontent">
            <div class="mt-3 text-center w-100">
              <h3 class="d-flex justify-center align-center">
                  {{item.name}}
              </h3>
              <p class="font-weight-thin text-grey">{{ item.text }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script setup>
    import { onMounted, ref, inject } from 'vue';

    const theme = inject('theme')

    const list = ref([
      {name: 'Estudo da Lei', icon:'mdi-link-variant', color: '#f01468', url: 'https://estudodalei.com.br/', text: 'legislaçao e questões'},
      {name: 'Stephane Lima', icon:'mdi-link-variant', color: '#f01468', url:'https://ste-site.netlify.app/', text: 'apresentação de mentoria'},
      {name: 'Day-to-do', icon:'mdi-link-variant', color: '#f01468', url: 'https://daytodo.estudodalei.com.br/', text: 'gerenciador de  finanças'},
      {name: 'Oh My Search', icon:'mdi-link-variant', color: '#f01468', url: 'https://legislacao.estudodalei.com.br/', text: 'busca na legislação'},
      {name: 'Revisão', icon:'mdi-link-variant', color: '#f01468', url: 'https://revisao.estudodalei.com.br/', text: 'metas e revisão para concursos'},
      {name: 'Convite', icon:'mdi-link-variant', color: '#f01468', url: 'https://theoniver.netlify.app/', text: 'convite de aniversário'}
    ])

    onMounted(()=> {
        document.getElementById("cards").onmousemove = e => {
            for(const card of document.getElementsByClassName("card")) {
                const rect = card.getBoundingClientRect(),
                    x = e.clientX - rect.left,
                    y = e.clientY - rect.top;

                card.style.setProperty("--mouse-x", `${x}px`);
                card.style.setProperty("--mouse-y", `${y}px`);
            };
        }
    })

    const goTo = (item) => {
      const win = window.open(item, '_blank');
      win.focus();
    }

</script>

<style lang="scss" scoped>
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
  width: 300px;
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
  min-height: calc(100% - 2px);
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
  min-height: 30%;
}
.card-content .img{
  min-height: 70%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>