<template>
    <div class="boxy">
            {{character.name}}<br>
           {{character.height}}cm
    </div>    
</template>

<script>
export default {
    name:'film-character',
    props:['character']
}
</script>

<style scoped>
.boxy{
    display:flex;
    justify-content:center;
    align-items:center;
    margin:10px;
    padding:10px;
    width:150px;
    height:150px;
    border-radius:30px;
    background-color:lightseagreen;
    box-shadow:4px 4px 5px red,inset 0px 0px 50px white;
    
}   
</style>