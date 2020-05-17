<template>
  <div v-if="episode">
      <select v-on:change="episodeSelect" v-model.number="selectedIndex">
    <option value="" disabled>Select a episode....</option>
        <option v-for="(episode, index) in episode[0].episode" :key="index" :value="index">
          {{episode.replace("https://rickandmortyapi.com/api/episode/", "Episode " )}}
        </option>
     </select>

  </div>
</template>

<script>
import {eventBus} from "@/main.js"
export default {
    name:"episode",
    props: ['episode'],

     data: function() {
        return{
            selectedIndex: ""
        }
    },

     methods:{
        episodeSelect: function(){
            eventBus.$emit('episode-select', this.selectedIndex) 
        }

    }
}


</script>

<style>

</style>