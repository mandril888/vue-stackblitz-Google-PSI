<template>
	<div class="api-call">
		<p>__________</p>
		<div id="event-handling">
			<p>{{ reversibleText }}</p>
			<button v-on:click="reverseText">Reverse Text</button>
		</div>
		<div id="list-rendering">
			<ol>
				<li>First item</li>
				<li v-for="user in users">
					<p>{{ user }}</p>
				</li>
			</ol>
		</div>
		<div class="card text-center m-3">
			<h5 class="card-header">Simple GET Request</h5>
			<div class="card-body">Total vue packages: <span>{{ simpleJson.title }}</span>
			</div>
		</div>
		<div class="card text-center m-3">
			<h5 class="card-header">Simple POST Request</h5>
			<div class="card-body">Returned Id: <span>{{ articleId }}</span></div>
		</div>
	</div>
</template>

<script>
	import axios from 'axios'
  
	export default {
    name: 'ApiCall',
    props: {
      reversibleText: String
    },
    data() {
      return {
        reversibleText: 'Hello Vue.js!',
        users: [],
        simpleJson: {},
        articleId: null
      }
    },
    created() {
      axios.get("https://jsonplaceholder.typicode.com/todos/1")
        .then(response => this.simpleJson = response.data);

      const article = { title: "Vue POST Request Example" };
      axios.post("https://reqres.in/api/articles", article)
        .then(response => this.articleId = response.data.id);

      const baseURI = 'https://jsonplaceholder.typicode.com/users'
      axios.post(baseURI)
      .then((result) => this.users = result.data.id)
    },
    methods: {
      reverseText() {
        this.reversibleText = this.reversibleText
          .split('')
          .reverse()
          .join('')
      }
    }
  }
</script>

<style scoped>
	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		text-align: left !important;
	}

	a {
		color: #42b983;
	}

	span {
		color: red;
	}
</style>