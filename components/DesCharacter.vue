<template>
    <v-card class="cardcita">
        <v-row class="rowtitle">
            {{ character.name }}
        </v-row>
        <v-row class="rowname">
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
                                <li class="li"> Cantidad de comics: </li>
                                <h2 class="li">{{ character.comics.available }}</h2>
                                <li class="li"> Cantidad de series: </li>
                                <h2 class="li">{{ character.series.available }}</h2>
                                <v-row text-align="center" color="#000" v-for=" (serie, index) in character.series.items" :key="index">
                                    <v-col cols="12" v-if="index < 3">
                                        <h2 class="li">{{ index + 1 }}. {{ serie.name }}</h2>
                                    </v-col>
                                </v-row>
                                <li class="li"> Cantidad de historias: </li>
                                <h2 class="li">{{ character.stories.available }}</h2>
                                <li class="li"> Cantidad de eventos: </li>
                                <h2 class="li">{{ character.events.available }}</h2>
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
    border-radius: 0% !important;
    display: flex !important;
    width: 750px !important;
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
    color:black
}
.carddes{
    background-color: white !important;
    color: black !important;
    
}
.li{
    font-family: "Arial Black" !important;
    color:black !important;
}
</style>