<template>
    <div>
        <CardComponent :face="cardTypes[0]"></CardComponent>
    </div>
</template>

<script setup lang="ts">
    import CardComponent from "./components/CardComponent.vue"

    const cardTypes = [
        '1_pig.png',
        '2_squirrel.png',
        '3_rabbit.png',
        '4_frog.png',
        '5_fox.png',
        '6_bear.png',
        '7_monkey.png',
        '8_panda.png',
        '9_chiken.png',
        '10_tiger.png',
        '11_pinguin.png',
        '12_racoon.png',
    ];
    const memoryCards = [...cardTypes, ...cardTypes];
</script>

<style scoped>
    
</style>