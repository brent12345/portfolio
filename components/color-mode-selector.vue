<script setup>
const colorMode = useColorMode()
const modes = [
    'system',
    'light',
    'dark'
]
const nextModeIcons = {
  system: '🌓',
  light: '🌕',
  dark: '🌑'
}

const nextMode = computed(() => {
    let nextModeIndex = null
    const currentModeIndex = modes.indexOf(colorMode.preference)
    if ( currentModeIndex + 1 === modes.length) {
        nextModeIndex = 0
    } else {
        nextModeIndex = currentModeIndex + 1
    }

    return modes[nextModeIndex]
    
})

const toggleMode = () => {
    colorMode.preference = nextMode.value
}

const nextModeIcon = computed(() => nextModeIcons[nextMode.value])
const showNextModelLabel = ref(false)


</script>
<template>
<div class="flex space-x-2 items-center">
    <div class="text-gray-500 text-xs" v-if="showNextModelLabel">Change to: {{ nextMode }}</div>
    <button @click="toggleMode" @mouseenter="showNextModelLabel = true" @mouseleave="showNextModelLabel = false" class="hover:bg-gray-100, dark:hover:bg-gray-500 px-2 py-1 text-gray-500"> {{ nextModeIcon  }}</button>
</div>
</template>
