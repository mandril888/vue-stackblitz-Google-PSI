<template>
	<div class="api-call">
		<p>__________</p>
		<div id="event-handling">
			<p>{{ message }}</p>
			<button v-on:click="reverseMessage">Reverse Message</button>
		</div>
		<div id="list-rendering">
			<ol>
				<li>aaa</li>
				<li v-for="user in users">
					<p>{{ user.name }}</p>
				</li>
			</ol>
		</div>
	</div>
</template>

<script>
	export default {
    name: 'ApiCall',
    props: {
      msg: String
    },
    data() {
      return {
        message: 'Hello Vue.js!',
        users: []
      }
    },
    methods: {
      fetchUsers: function () {
        const baseURI = 'https://jsonplaceholder.typicode.com/users'
        this.$http.get(baseURI)
        .then((result) => {
          this.users = result.data
        })
      },
      reverseMessage() {
        this.message = this.message
          .split('')
          .reverse()
          .join('')
      }
    }
  }
</script>

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