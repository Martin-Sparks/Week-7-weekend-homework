<template>
  <div>

      <select id="select-charactor" >
        <option value="charactor.name" v-for="charactor in charactorName.results" :key="charactor.name">
          {{charactor.name}}
        </option>
     </select>
      <ul>
          <li v-for="charactor in charactorName.results" :key="charactor.name"> 
                {{charactor.name}}
          </li>
      </ul>
  </div>
</template>

<script>
import {eventBus} from "@/main.js"
export default {
    name: "get-charactor",
    props: ["charactorName"]

}
</script>

<style>

</style>