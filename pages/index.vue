<template>
    <div class="mt-3 text-center">
        <br>
        <br>
        <br>
        <v-container class="container">
            <v-row>
                <v-col v-for="item in characters" :key="item.id">
                    <v-card width="250" height="250" elevation-19 @click="openDialog(item)" :title="item.name" class="card">
                        <v-img width="150" class="img" :src="item.thumbnail.path + '.' + item.thumbnail.extension"
                            cover ></v-img>
                    </v-card>
                </v-col>
            </v-row>
        </v-container>


    </div>
</template>
<script setup>
import axios from 'axios';

onBeforeMount(() => {
    getCharacters();
});

const publicApiKey = "8aa3287210c556e7bcdce81eefc66567";
const HASH = "a7ad700b81bed5a917cf24d2ce28de66";
const url = `https://gateway.marvel.com:443/v1/public/characters?ts=1&apikey=${publicApiKey}&hash=${HASH}&limit=100`;
const characters = ref([]);
const currentCharacter = ref(null);

const dialog = ref(false);

const getCharacters = async () => {
    const { data } = await axios.get(url)
    characters.value = data.data.results.filter(character => {
        return !character.thumbnail.path.includes("image_not_available");
    })

}
const openDialog = (character) => {
    currentCharacter.value = character;
    dialog.value = true;
}
</script>
<style>
.card {
    border-radius: 100px !important;
    display: flex !important;
    align-items: center !important;
    justify-content: center !important;
    flex-direction: column !important;
    padding: 10px !important;
    border: solid 2px black !important;
    background-color: hsl(0, 0%, 0%) !important;
    box-shadow: 5px 5px 5px 5px rgba(0, 0, 0, 0.3) !important;
}

.img {
    border-radius: 50px;
    margin-bottom: 1px;
}
* {
    
    font-family: "Arial Black" !important;
    color: white !important;

}
.container{
    align-items: justify !important;
    justify-content: justify !important;
    flex-direction: column !important;
}

</style>;

