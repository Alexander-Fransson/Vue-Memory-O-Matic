<template>
    <div @click="flip">
        <img :src="face"/>
    </div>
</template>

<script setup lang="ts">
    const cardProps = defineProps<{id: number, face: string, back: string, paired:boolean}>();
    const cardEmits = defineEmits(['flip']);
    const flip = () => {
        cardEmits('flip',cardProps.face,cardProps.id);
    }
</script>

<style scoped>
    
</style>