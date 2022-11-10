<template>
    <div>
        <CardComponent @flip="flip" v-for="cards in memoryRef" :id="cards.id" :face="cards.face" :back="cards.back" :paired="cards.paired"></CardComponent>
    </div>
</template>

<script setup lang="ts">
    import CardComponent from "./CardComponent.vue";
    import {ref} from 'vue';

    const faceTypes = [
        'img/1_pig.png',
        'img/2_squirrel.png',
        'img/3_rabbit.png',
        'img/4_frog.png',
        'img/5_fox.png',
        'img/6_bear.png',
        'img/7_monkey.png',
        'img/8_panda.png',
        'img/9_chick.png',
        'img/10_tiger.png',
        'img/11_penguin.png',
        'img/12_racoon.png',
    ];
    const memoryFaces = [...faceTypes, ...faceTypes];

    interface ICards {
        id: number;
        face: string,
        back: string,
        paired: boolean,
    }

    const memoryCards:ICards[] = [];
    memoryFaces.forEach(face => memoryCards.push({id:Math.ceil(Math.random()*1000000), face:'img/back.png', back:face, paired:false}));
    const memoryRef = ref(memoryCards).value;

    const flip = (face: string, id: number) => {
        if(memoryRef.filter(card => card.face != 'img/back.png').length < 2){
            memoryRef.map(card => {
            if(card.id == id){
                const faceHolder = card.face;
                card.face = card.back;
                card.back = faceHolder;
                }
            })   
        }
        if(memoryRef.filter(card => card.face != 'img/back.png').length == 2){
            memoryRef.map(card => {

                setTimeout(() => {
                    if(card.face != 'img/back.png'){
                        const faceHolder = card.face;
                        card.face = card.back;
                        card.back = faceHolder;
                    }
                }, 2000);
            })
        }
    }
</script>

<style scoped>
    div{
        display:flex;
        flex-wrap: wrap;
    }
</style>