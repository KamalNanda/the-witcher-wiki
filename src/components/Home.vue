<template>
	<div id="home">
	<div id="searchbar">
        <input v-model="searchQuery" type="text" placeholder="Search Character" />
    </div>
		<div id="home-grid">
			<div class="grid-element" v-for="wdata in resultQuery" :key="wdata.id"   >
				<router-link :to="{name: 'About' , params: { wdata }}"  class="r-link">
					<img class="img" v-bind:src="wdata.imgLink" />
					<h1>{{wdata.name}}</h1>
					<p>{{wdata.role}}</p>
				</router-link>
			</div>
		</div>	
	</div>
</template>
<script>
	import Wdatas from './witcherdata.js'; 
	export default {
		name: 'Home',  
		data(){
			return{
				searchQuery : null, 
			}
		},
		computed : {
			resultQuery(){
				if(this.searchQuery){
					return Wdatas.filter((item)=>{
						return this.searchQuery.toLowerCase().split(' ').every(v => item.name.toLowerCase().includes(v))
					})
				}else{
					return Wdatas;
				}
			}
		}
	}
</script>	
<style> 
  #home{
		width: 80%;
		margin: 40px 10%;
		font-family: monospace; 
	}
	 #searchbar input{
        width: 30%;
        padding: 5px 10px;
        font-size: 16px;
        margin: 40px auto;
        height: 40px;
        border:none;
        border-radius: 15px
    }
	#home-grid{
			display: grid;
			grid-template-columns: 1fr 1fr 1fr;
			grid-column-gap: 20px;
			grid-row-gap:20px;
		}
		.grid-element{
			background:black;
			text-align: left;
			color: white;
		}
		.img{width: 100%}
		.grid-element h1{
			margin-top: 4px;margin-bottom: 0;padding-left: 20px;
		}
		.grid-element p{
			margin-top: 2px;
			color: gray;padding-left: 20px;
		}
		.grid-element:hover{
			transform: scale(1.2)
		}
		@media (max-width: 786px){
			#home-grid{
				grid-template-columns: 1fr 1fr;
			}
			#searchbar input {
				width : 70%;
			}
		}
		@media (max-width: 525px){
			#home-grid{
				grid-template-columns: 1fr;
			}
		}
</style>
