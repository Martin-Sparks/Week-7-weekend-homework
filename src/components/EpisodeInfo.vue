<template>
   <div id="episode-info" v-if="episodeinfo.length !== 0">
        <h2>Episode Star List</h2>

        <ul>
                <li v-for="(charactor, index) in episodeinfo" :key="index" :value="index"> 
                    <div class="row">
                        <div class="col-6">character: {{ charactor.name}}</div>
                        <div class="col-6"><img :src="charactor.image" alt="image" width="100px" height="100px" class="pull-right"></div>
                    </div>
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

li {
    list-style: none
}

</style>