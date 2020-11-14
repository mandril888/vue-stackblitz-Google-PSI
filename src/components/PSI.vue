<template>
	<div class="psi">
		<div id="PSI-info">
			<p>Web: {{ infoFromTest.id }}</p>
			<p>LARGEST_CONTENTFUL_PAINT_MS:
				{{ infoFromTest.loadingExperience }}</p>
		</div>
		<div class="h-100"></div>
	</div>
</template>

<script>
	import axios from 'axios'
  
	export default {
    name: 'psi',
    data() {
      return {
        infoFromTest: {}
      }
    },
    created() {
      const psiApiUrl = "https://pagespeedonline.googleapis.com/pagespeedonline/v5/runPagespeed?url=https://seocom.agency";

      axios.get(psiApiUrl)
        .then(response => 
          this.infoFromTest = response.data
        );
    }
  }
</script>

<style scoped>
	#PSI-info {
		text-align: left;
	}

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