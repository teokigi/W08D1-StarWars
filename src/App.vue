<template>
  <body id="app">
    <h1>Star Wars</h1>
    <div>
        <h2>Films Listing:</h2>
        <FilmList :films="this.films" v-if="films"/>
    </div>
    <div>
        <h2>Film details:</h2>
        <FilmDetail :film="selected" v-if="selected"/>
    </div>
  </body>
</template>

<script>

import FilmList from '@/components/FilmList.vue';
import {eventBus} from '@/main.js';
import FilmDetail from '@/components/FilmDetail.vue';

export default {
  
  
  name: 'App',
  
  data(){return{
    films: null,
    selected: null,
  }},

  mounted(){
    this.getFilms()

    eventBus.$on('FilmItemClickAction', clickedFilm => this.setSelected(clickedFilm))
  },

    methods:{
        getFilms(){
            fetch("https://swapi.dev/api/films/")
            .then(res => res.json())
            .then(resData => this.films=resData)
        },
        setSelected(clickedFilm){
            this.selected = this.selected ? null : clickedFilm
        }
    },

  components:{
    FilmList, FilmDetail
  }
  
}
</script>

<style>
body {
    width:1200px;
    text-align:center;
    background-color:grey;
}
h1{
    letter-spacing:10px;
    text-shadow: 0px 0px 10px blue;
}
h2{
    text-shadow: 0px 0px 10px lightcoral;
}
h3{
    text-shadow: 0px 0px 10px green;
}

</style>
// MVP
//Done - The app should initially display a list of the film titles

//Done - When a film title is clicked the app should load the film details including title, episode number, release date and director.

//Done -  When the film detail loads, the films characters details (name and height) should also be displayed.

// Extensions
//ToDo -  Add a filter to format the height from centimetres into meters (i.e. 172cm => 1.72m)
//ToDo -  Add a filter to format the date as dd MMM YYYY. (19 May 1999) (Hint- Look into Moment npm package)
//ToDo -  Also show details of a characters home world (name, terrain) along with the character name and height.
// Advanced Extensions
//ToDo -  Use router to add a link to the film details. When this is clicked it should take you to a view that displays the films opening crawl text. (Doesn’t need to be fancy!). The crawl view should take in the film as a prop to access the crawl.