<template>
    <div class="mt-3 text-center">
        <br>
        <br>
        <br>
        <v-container class="container">
            <v-row>
                <v-col v-for="item in characters" :key="item.id" class="col">
                    <v-card width="250" height="250" @click="openDialog(item)" :title="item.name" class="card">
                        <v-img width="150" class="img" :src="item.thumbnail.path + '.' + item.thumbnail.extension"
                            cover></v-img>
                    </v-card>
                </v-col>
                <v-card style="border-radius: 50px !important;">
                    <v-dialog v-model="dialog" width="auto"
                        style="background: none !important; border-radius: 80px !important;">
                        <des-character :character="currentCharacter"></des-character>
                        <v-btn color="#000" class="btn" block @click="dialog = false">Cerrar</v-btn>
                    </v-dialog>
                </v-card>
            </v-row>
        </v-container>


    </div>
</template>
<script setup>
import axios from 'axios';
import DesCharacter from '~/components/DesCharacter.vue';

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
    border-radius: 80px !important;
    display: flex !important;
    align-items: center !important;
    justify-content: center !important;
    flex-direction: column !important;
    border: solid 2px black !important;
    background-color: hsl(0, 0%, 0%) !important;
    box-shadow: 5px 5px 5px 5px rgba(0, 0, 0, 0.3) !important;
    padding-left: 15px !important;
    padding-right: 15px !important;
}

.btn {
    font-family: "Arial Black" !important;
    color: black !important;
    background-color: #C40000 !important;

}

.img {
    border-radius: 50px !important;
    margin-bottom: 1px !important;
}

* {

    font-family: "Arial Black" !important;
    color: white !important;
    font-size: 16px !important;
    font-style: oblique !important;
}

.container {
    align-items: justify !important;
    justify-content: justify !important;
    flex-direction: column !important;
}

.col {
    padding-right: 2px !important;
    margin: 2px !important;
}

*::-webkit-scrollbar {
    width: 28px;
    background: transparent !important;
}

*::-webkit-scrollbar-thumb {
    box-shadow: inset 0 0 0 10px #c9c6c6 !important;
    border: 10px solid transparent !important;
    border-radius: 40px;
}

*:hover::-webkit-scrollbar-thumb:hover {
    box-shadow: inset 0 0 0 10px #333 !important;
    border: 8px solid transparent !important;
}

*::-webkit-scrollbar-track {
    background-color: transparent !important;
}</style>;

