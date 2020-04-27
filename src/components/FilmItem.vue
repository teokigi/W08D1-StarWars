<template>
    <div class="FilmItem" v-if="film" v-on:click="clickHandler">
        {{film.title}}
    </div>    
</template>

<script>
import {eventBus} from '@/main.js'

export default {
    name:'film-item',
    props:['film'],
    methods:{
        clickHandler(){
            eventBus.$emit('FilmItemClickAction', this.film)
        }
    }
}
</script>

<style scoped>
.FilmItem{
    display:flex;
    justify-content:space-around;
    align-items:center;
    color:#112244;
    font-family:georgia;
    padding:5px;
    margin:5px;
    width:200px;
    height:40px;
    border-radius:30px;
    background-color:#999977;
}
</style>