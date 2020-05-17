<template>
   <div id="episode-info" v-if="episodeinfo.length !== 0">
        <h2>Eposode Info..</h2>

        <ul>
                <li v-for="(charactor, index) in episodeinfo" :key="index" :value="index"> charactor...{{charactor.name}}
                    <img :src="charactor.image" alt="image" width="100px" height="100px">
                </li>
            
        </ul>

 </div>
</template>

<script>
import {eventBus} from "@/main.js"
export default {
    name:"episode-info",
    props: ["episodeinfo"]

}
</script>

<style>

</style>