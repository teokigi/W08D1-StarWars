<template>
    <div class="FilmListing">
        <FilmItem v-for="film of films.results" :film="film" v-if="films"/>
    </div>

</template>

<script>
import FilmItem from '@/components/FilmItem.vue'
export default {
    name:'film-list',
    props:['films'],
    components:{
        FilmItem
    }
}
</script>

<style scoped>
.FilmListing{
    display:flex;
    flex-direction:row;
    height: 70px;
    background-color:#115599;
    border-radius:30px;
    margin:5px;
    padding:5px;
}
</style>