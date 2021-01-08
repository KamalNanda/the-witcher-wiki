<template>
	<div id="About">
		<div class="about-flex-left">
			<img v-bind:src="wdata.imgLink" class="img"/>
		</div>
		<div class="about-flex-right">
			<div class="about-flex-right-content">
				<h1>{{name}}</h1>
				<h2>{{role}}</h2>
				<p>{{details}}</p>
			</div> 
			<Gallery v-bind:images="wdata.gallery"/>
		</div>
	</div>
</template>
<script>
	import Gallery from './Gallery'
export default { 
	name: 'About',
	props: ['wdata'],
	components:{
		Gallery
	},
  data(){
	  return{
		imgLink: '',
	 	name: '',
	    role: '',
		details: ''
	  }
  },
  mounted(){
	  if(this.wdata){
		this.imgLink = this.wdata.imgLink
		this.name = this.wdata.name 
	  	this.role = this.wdata.role
	  	this.details = this.wdata.details
	  }
  }
}
</script>
<style>
	#About{
		display: flex;
		width:80%;
		margin: 60px 10%;
		color: white;
	}
	.about-flex-left{
		width:50%;
	}
	.about-flex-right{
		width: 50%;
		background-color:black;
		display: grid;
		align-items: center;
		text-align: left;
	}
	.about-flex-right h1{font-size: 42px;margin-top: -5px;}
	.about-flex-right p{font-size: 18px;}
	.about-flex-right h2{font-size: 32px;color: gray;margin-top: -35px;}
	.about-flex-right-content{
		margin-left: 20px;
		margin-right: 20px
	}
	@media (max-width:500px){
		#About h1{font-size: 30px;}
		#About h2{font-size: 24px;margin-top: -20px;}
		#About{display: block;}
		.about-flex-right , .about-flex-left{width: 100%;}
	}
</style>