<script setup lang="ts">
import type { Result as Character } from "@/characters/interfaces/character";
import { toRef } from "vue";
import { useRouter } from "vue-router";


const props = defineProps<{
    character: Character
}>();

// toRef es exclusivo para capturar propiedades de props y aislar
const character = toRef(props, "character");

const router = useRouter();

const goTo = () => {
    router.push(`by/${ character.value.id }`);
}

</script>

<template>
    <div class="character-card" @click="goTo()">
        <img :src="character.image" :alt="character.name">
        <h3>{{ character.name }}</h3>
    </div>
</template>


<style scoped>
.character-card {
    display: flex;
    flex-direction: column;
    align-items: center;
    cursor: pointer;
}

img {
    width: 250px;
    border-radius: 5px 5px 0px 0px;
    box-shadow: 0px 2px 10px rgb(255, 255, 255, 0.1);
    transition: all .5s;
}

img:hover {
    box-shadow: 0px 2px 10px rgb(255, 255, 255, 0.5);
    transition: all .5s;
}
</style>