<template>
    <div class="headerWrapper" :class="theme == 'dark' ? '': 'bg-white border'">
        <div class="subHeader">
            <v-avatar><span class="text-red font-weight-bold">JHJ</span></v-avatar>
            <v-btn 
                variant="text" :icon="iconDark"
                @click="darkModeChange()"
            >
            </v-btn>
        </div>
    </div>
</template>

<script setup>
    import { computed, ref, inject } from 'vue'

    const theme = inject('theme')
    
    const darkMode = ref(true)

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
</style>