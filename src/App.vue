<template>
  <div id="app">
	<nav>
		<div class="nav">
			<div class="nav-left">
				<router-link to="/"  ><img src="./assets/logo.png" /></router-link>
			</div>
			<div class="nav-right">
				<router-link to="/" class="r-link" >Home</router-link>
			</div>
		</div>
	</nav>
    <router-view></router-view>
	<footer>Made with ❤️ by Oindrila Ray with VueJS</footer>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
footer{
	color: gray;
	background-color: black;
	font-size: 24px;
	height: 30px;
	padding: 3px;
}
footer .r-link{padding: 0;}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  height:auto;
  padding:0;
  margin:0;
  background-color:grey
}
.r-link{
	color: white;
	text-decoration: none;
	width: 129px;
    padding: 18px 0px;
}
nav .r-link:hover{
	color: black;
	background-color: white;
}
nav{background-color: black;}
.nav{
	width:80%;
	margin-left: 10%;
	color: white;
	font-size: 24px;
	height: 60px;
	padding: 10px;
	display:flex;
	justify-content: space-between;
}
.nav-left{
	width: 25%;
}
.nav-left img{
	width:100%;
	margin-top: -30px
}
.nav-right{
	width: 40%;
	text-align: center;
	height: 40px;
	display: grid;
	justify-items: center;
	align-items: center;
}
@media (max-width: 500px){
	.nav-right{display: none;}
	.nav-left{width: 100%;padding: 1.5% 0;}
	footer{font-size: 14px;}
}
</style>
