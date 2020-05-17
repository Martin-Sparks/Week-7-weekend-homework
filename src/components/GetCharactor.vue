<template>
  <div d="select-charactor">
      <select v-on:change="onNameSelect" v-model.number="selectedIndex">
    <option value="" disabled>Select a charactor...</option>
        <option v-for="(charactor, index) in charactorList" :key="index" :value="index">
          {{charactor.name}}
        </option>
     </select>
      <!-- <ul>
          <li v-for="charactor in charactorName.results" :key="charactor.name"> 
                {{charactor.name}}
          </li>
      </ul> -->
  </div>
</template>

<script>
import {eventBus} from "@/main.js"
export default {
    name: "get-charactor",
    props: ["charactorList"],

    data: function() {
        return{
            selectedIndex: ""
        }
    },
    
    methods:{
        onNameSelect: function(){
            eventBus.$emit('name-selected', this.selectedIndex)
            this.selectedIndex = "";
            
        }
    }
}
</script>

<style>

</style>