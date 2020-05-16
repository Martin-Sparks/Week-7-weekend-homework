<template>
<div>
  <h1>Hello World!</h1>
  <get-charactor :charactorName="rickAndMorty"></get-charactor>
  </div>
</template>

<script>

import {EventBus} from "@/main.js"
import GetCharactor from './components/GetCharactor.vue';

export default {
  name:"app",
  data(){
      return {
        rickAndMorty: {},
        results: {}
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
    .then(this.getCharacter())

  },

  components: {
    "get-charactor": GetCharactor

  }
}
</script>

<style>

</style>