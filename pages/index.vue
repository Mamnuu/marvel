<template>
    <div class="mt-3 text-center">

    </div>
</template>
<script setup>
import axios from 'axios';

onBeforeMount(() => {
    getCharacters();
});

const publicApiKey = "8aa3287210c556e7bcdce81eefc66567";
const HASH = "9c31d0c688b40de1d5ad29642ee576f8";
const url = `https://gateway.marvel.com:443/v1/public/characters?ts=1&apikey=${publicApiKey}&hash=${HASH}&limit=100`;
const characters = ref([]);
const currentCharacter = ref(null);
const flagApi = ref(true);
const dialog= ref(false)

const getCharacters = async () => {
    const { data } = await axios.get(url)
    characters.value = data.data.results.filter(character => {
        return !character.thumbnail.path.includes("image_not_available");
    })
    flagApi.value = false;
}

</script>
