<template>
    <div>
        <img :src="face"/>
    </div>
</template>

<script setup lang="ts">
    const cardProps = defineProps<{face: string}>()
</script>

<style scoped>
    
</style>