<template>
    <div id="Gallery">
        <h2>Image Gallery</h2>
        <div class="gallery-grid">
            <img v-on:click="popUpOpen" v-bind:src="img" v-for="img in this.img"  />
        </div> 
        <div id="img-popup">
            <h3 v-on:click="popUpClose">X</h3>
            <img v-bind:src="popupImg" />
        </div>
    </div>
    
</template>
<script> 
    export default {
        name : 'Gallery',
        props : ['images'],
        data(){
            return{
                img: [],
                popupImg: ''
            }
        },
        methods:{
            popUpOpen : function (event){
                document.getElementById('img-popup').style.display="block"
                this.popupImg= event.target.src
            },
            popUpClose : function (){
                document.getElementById('img-popup').style.display="none"
            }
        
        },
        mounted(){
            if(this.images){
                this.img = this.images
            }
        }
    } 
</script>
<style>
    #Gallery{
        width: 90%;
        margin:auto; 
    }
    #img-popup{
        position:absolute;
        display:none;
        top: 25%;
        left: 40%;
        width: 500px;
        height: 500px;
        z-index:10;
        background: white;
        box-shadow: 1px 3px 5px black
    }
    #img-popup h3{
        color: black;
        text-align: right;
        margin: 5px 10px; 
        cursor: pointer
    }
    #img-popup img{
        width : 90%;
        height : 85%;
        margin-left: 5%;
    }
    .gallery-grid{
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-gap: 20px;
        margin-bottom: 20px
    }
    .gallery-grid img{
        width: 100%;
        height: 180px;
        cursor: pointer
    }
    .gallery-grid img:hover{
        transform: scale(1.2)
    }
</style>