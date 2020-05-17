<template>
    <div id="charactor-info" v-if="charactorDetails">
        <h2>{{charactorDetails.name}}</h2>
        <ul>
            <li> Name: {{ charactorDetails.name}}</li>
            <br>
            <li> Status: {{ charactorDetails.status}}</li>
            <br>
            <li> Species: {{ charactorDetails.species}}</li>
            <br>
            <li> Gender {{ charactorDetails.gender}}</li>
            <br>
            <li> Origin {{ charactorDetails.origin.name}}</li>
            <br>
            <img :src="charactorDetails.image" alt="image">
            <p>Episodes appeared in: {{ charactorDetails.episode.length}}</p>
    </ul>
 </div>
  
</template>



<script>
import {eventBus} from "@/main.js"
export default {
    name:"charactor-info",
    props: ["charactorDetails"]

}
</script>

<style>

</style>