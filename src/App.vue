<template>
<div id="main">
  <h1 class="text-center">Pickle Rick.com</h1>
  <div class="row">
    <div class="col-5 offset-1">
      <get-charactor :charactorList="rickAndMorty.results"></get-charactor>
      <charactor-info :charactorDetails="selectedCharactor"></charactor-info>
     </div>
    <div class="col-5 offset-1">
      <episode :episode="rickAndMorty.results"> </episode>
      <episode-info :episodeinfo="selelctedEpisodeInfo"> </episode-info>
    </div>
  </div>

  </div>
</template>

<script>

import {eventBus} from "@/main.js"
import GetCharactor from './components/GetCharactor.vue';
import CharactorInfo from './components/CharactorInfo.vue';
import Episode from './components/Episode.vue';
import EpisodeInfo from './components/EpisodeInfo.vue';
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

export default {
  name:"app",
  data(){
      return {
        rickAndMorty: {},
        results: {},
        selectedCharactor: null,
        selelctedEpisode: null,
        selelctedEpisodeInfo: []
      }
  },



  mounted(){
    fetch("https://rickandmortyapi.com/api/character/")
    .then(res => res.json())
    .then(rickAndMorty => {this.rickAndMorty = rickAndMorty})

    eventBus.$on('name-selected', (index) =>{
      this.selectedCharactor = this.rickAndMorty.results[index];
      
    }),

      eventBus.$on('episode-select', (index) =>{
    
        this.selelctedEpisodeInfo = []
        this.rickAndMorty.results.forEach(charactor => {
         if (charactor.episode.includes("https://rickandmortyapi.com/api/episode/" + (index +1)))
        this.selelctedEpisodeInfo.push({name: charactor.name, image:charactor.image})
            
      });
                
    })
  },

  components: {
    "get-charactor": GetCharactor,
    "charactor-info": CharactorInfo,
    "episode": Episode,
    "episode-info": EpisodeInfo
  }
}
</script>

<style>

   #main {
     min-height: 100vh;
      background-image: url("../public/thumb-1920-876590.jpg");
      background-size: cover;
      color: green;
  }

  .text-center {
    color: green;
  }

</style>