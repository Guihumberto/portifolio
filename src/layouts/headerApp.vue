<template>
    <div class="headerWrapper" :class="theme == 'dark' ? '': 'bg-white border'">
        <div class="subHeader">
            <v-avatar><span class="text-red font-weight-bold">JHJ</span></v-avatar>
            <v-btn 
                variant="text" :icon="iconDark"
                @click="darkModeChange()"
            >
            </v-btn>
            <v-btn v-if="tela" class="upBtn" color="success" variant="elevated" icon="mdi-arrow-up"  @click="findPage"></v-btn>
        </div>
    </div>
</template>

<script setup>
    import { computed, ref, inject, onMounted } from 'vue'

    onMounted(()=>{
        window.addEventListener('scroll', handleScroll);
    })

    const theme = inject('theme')
    
    const darkMode = ref(true)
    const tela = ref(false)

    const findPage = (item) => {
        window.scrollTo({
            top: 0,
            behavior: 'smooth'
        });
    }
    const handleScroll = () => {
        tela.value = window.scrollY > 0;
    }

    const iconDark = computed(() => {
        return darkMode.value 
        ? 'mdi-white-balance-sunny'
        : 'mdi-weather-night'
    })

    const emit = defineEmits(["darkmode"])

    const darkModeChange = (() => {
        darkMode.value = !darkMode.value
        emit('darkmode', darkMode)
    })


    
</script>

<style lang="scss" scoped>
.headerWrapper{
    position: fixed;
    padding:5px 10px;
    top: 0;
    width: 100%;
    z-index: 1000;
    background: #121212;
}
.subHeader{
    width: min(100%, 1080px);
    margin-inline: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.upBtn{
  position: fixed;
  bottom: 1.5rem;
  right: 1.5rem;
  z-index: 1000;
  transition: 1s ease;
  opacity: 0;
  animation: slideTop .5s ease forwards;
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

/* Transição fade */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}

/* Estilo da div que vai desaparecer */
.fade-div {
  padding: 20px;
  background-color: #f1c40f;
  color: white;
  position: fixed;
  top: 50px;
  left: 50px;
  z-index: 1000;
}
</style>