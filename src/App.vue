<template>
<div>
  <h1>Pickle Rick.com</h1>
  <get-charactor :charactorList="rickAndMorty.results"></get-charactor>
  <charactor-info :charactorDetails="selectedCharactor"></charactor-info>
  <episode :episode="rickAndMorty.results"> </episode>
  <episode-info :episodeinfo="selelctedEpisodeInfo"> </episode-info>


  </div>
</template>

<script>

import {eventBus} from "@/main.js"
import GetCharactor from './components/GetCharactor.vue';
import CharactorInfo from './components/CharactorInfo.vue';
import Episode from './components/Episode.vue';
import EpisodeInfo from './components/EpisodeInfo.vue';

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

</style>