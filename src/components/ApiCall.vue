<template>
	<div class="hello">
		<p>__________</p>
		<h1>{{ msg }}</h1>
		<p>__________</p>
	</div>
</template>

<script>
	export default {
  name: 'ApiCall',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	.hello p {
		text-align: center;
	}

	h3 {
		margin: 40px 0 0;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		display: inline-block;
		margin: 0 10px;
	}

	a {
		color: #42b983;
	}
</style>