<template>
<div>
  <h1>Pickle Rick.com</h1>
  <get-charactor :charactorList="rickAndMorty.results"></get-charactor>
  <charactor-info :charactorDetails="selectedCharactor"></charactor-info>
  </div>
</template>

<script>

import {eventBus} from "@/main.js"
import GetCharactor from './components/GetCharactor.vue';
import CharactorInfo from './components/CharactorInfo.vue';

export default {
  name:"app",
  data(){
      return {
        rickAndMorty: {},
        results: {},
        selectedCharactor: null
      }
  },

  methods: {
      getCharacter: function(){
          // this.rickAndMorty.results(element => {
          //     console.log(element.name);

          // });
          
      }
  },

  mounted(){
    fetch("https://rickandmortyapi.com/api/character/")
    .then(res => res.json())
    .then(rickAndMorty => {this.rickAndMorty = rickAndMorty})
    .then(this.getCharacter());

    eventBus.$on('name-selected', (index) =>{
      this.selectedCharactor = this.rickAndMorty.results[index];
      // console.log(index);
      console.log(this.rickAndMorty.results[index]);
      
      
    })
  },

  components: {
    "get-charactor": GetCharactor,
    "charactor-info": CharactorInfo
  }
}
</script>

<style>

</style>