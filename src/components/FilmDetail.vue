<template>
    <div class="FilmDetail">
        <div class="filmTitle">
           <h3>Title: {{film.title}}</h3>
        </div>
        <div class="filmEpisodeNum">
            <h3>Episode: #{{film.episode_id}}</h3>
        </div>
        <div class="filmReleaseDate">
            <h3>Release Date: {{film.release_date}}</h3>
        </div>
        <div class="filmDirector">
            <h3>Director: {{film.director}}</h3>
        </div>
        <h3> Characters and their height </h3>
        <div class="CharacterField">
            <FilmCharacter class="charBox" v-for="(character, index) of characters" :character="character" :key="index"/>
        </div>
    </div>
</template>

<script>
import FilmCharacter from '@/components/FilmCharacters.vue'

export default {
    name:'film-detail',
    props:['film'],
    data(){
        return{
            characters: null,
        }
    },
    mounted(){
        this.getCharacter()
    },
    methods:{
        getCharacter(){
            const characterPromises = this.film.characters.map((char =>{
                return fetch(char)
                .then(res => res.json());
            }))
            Promise.all(characterPromises)
            .then(charData => this.characters=charData)
            
        }
    },
    components:{
        FilmCharacter
    }
}
</script>

<style scoped>
.FilmDetail{
    text-align:left;
    color:blue;
}
.FilmCharacter{
    color:coral;
}
.CharacterField{
    display:flex;
    flex-flow:wrap;
    margin:5px;
    width:95%;
    height:200px;
    overflow-y:scroll;
    border-radius:30px;
    background-color:#222222;
}
.CharacterField::-webkit-scrollbar{
    display:none;
}
</style>

//characters details (name and height) should also be displayed.