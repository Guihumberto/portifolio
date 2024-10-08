<template>
    <div class="headerWrapper">
        <div class="subHeader">
            <v-avatar>JHJ</v-avatar>
            <v-btn 
                variant="text" :icon="iconDark"
                @click="darkModeChange()"
            >
            </v-btn>
        </div>
    </div>
</template>

<script setup>
    import { computed, ref } from 'vue'
    
    const darkMode = ref(false)

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
}
.subHeader{
    width: min(100%, 1080px);
    margin-inline: auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>