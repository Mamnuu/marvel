<template>
    <v-card class="cardcita">
        <v-row class="rowtitle">
            {{ character.name }}
        </v-row>
        <v-row>
            <v-col cols="6" style="text-align: center;">
                <v-row>
                    <v-col>
                        <p>
                        <h3>{{ character.description || 'No encontramos descripción para este personaje' }}</h3>
                        </p>
                    </v-col>
                </v-row>
                <v-row>
                    <v-col>
                        <v-card class="carddes" >
                            <ul>
                                <li class="li">  Cantidad de comics: {{ character.comics.available }} </li> <br>
                                <li class="li"> Cantidad de series: {{ character.series.available }} </li> <br>
                                <v-row text-align="center" color="#000" v-for=" (serie, index) in character.series.items" :key="index"> 
                                    <v-col cols="12" v-if="index < 3">
                                        <h2 class="li">  {{ index + 1 }}. {{ serie.name }}</h2>
                                    </v-col>
                                </v-row>
                                <br>
                                <li class="li"> Cantidad de historias: {{ character.stories.available }} </li> <br>
                                <li class="li"> Cantidad de eventos: {{ character.events.available }} </li>
                            </ul>
                        </v-card>
                    </v-col>
                </v-row>
            </v-col>
            <v-col cols="4">
                <v-img width="100%" height="100%" aspect-ratio="3/4" class="imgdes" cover
                    :src="character.thumbnail.path + '.' + character.thumbnail.extension"></v-img>
            </v-col>
        </v-row>
    </v-card>
</template>
<script>
export default {
    props: {
        character: Object
    }
}
</script>
<style>

.cardcita {
    border-radius: 0px !important;
    display: flex !important;
    width: 800px !important;
    height: 450 !important; 
    align-items: "justify-content" !important;
    justify-content: center !important;
    flex-direction: column !important;
    border: solid 2px black !important;
    background-color: hsl(0, 0%, 0%) !important;
    box-shadow: 5px 5px 5px 5px rgba(0, 0, 0, 0.3) !important;
    padding-left: 15px !important;
    padding-right: 15px !important;
    padding-top: 15px !important;
}
.imgdes {
    border-radius: 50px !important;
    margin-bottom: 1px !important;
    margin-left: 30% !important;
}
.rowtitle{
    font-size: 22px !important;
    align-items:  center !important; 
    margin: auto !important; 
    color:rgb(255, 253, 253)
}
.carddes{
    background-color: rgb(0, 0, 0) !important;
    color: rgb(255, 255, 255) !important;
    display: flex !important;
    align-items: center !important;
    justify-content: center !important;
    flex-direction: column !important;
}
.li{
    font-family: "Arial Black" !important;
    color:rgb(255, 255, 255) !important;
    text-align: justify !important;
}
*::-webkit-scrollbar {
  width: 28px;
  background: transparent;
}

*::-webkit-scrollbar-thumb {
  box-shadow: inset 0 0 0 10px #c9c6c6;
  border: 10px solid transparent;
  border-radius: 40px;
}

*:hover::-webkit-scrollbar-thumb:hover {
  box-shadow: inset 0 0 0 10px #333;
  border: 8px solid transparent;
}

*::-webkit-scrollbar-track {
  background-color: transparent;
}
</style>