<template>
	<div id="app">
		<HelloWorld msg="Welcome to Your Vue.js App" />
		<PSI msg="Welcome to Your Vue.js App" />
		<ApiCall msg="Welcome to Your Vue.js App" />
	</div>
</template>

<script>
	import HelloWorld from './components/HelloWorld.vue'
  import ApiCall from './components/ApiCall.vue'
  import PSI from './components/PSI.vue'

  export default {
    name: 'App',
    components: {
      HelloWorld,
      ApiCall,
      PSI,
    }
  }
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}

  .h-100 {
    height: 100px;
  }
</style>