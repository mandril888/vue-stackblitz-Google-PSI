<template>
	<script src="//script.sheetsu.com/"></script>
	<div class="psi">
		<p>See the <a href="https://github.com/mandril888/vue-stackblitz-Google-PSI" target="_blank">repo</a> in my
			GitHub.</p>
		<p>I used:</p>

		<ul>
			<li>
				<a href="https://v3.vuejs.org/guide/introduction.html" target="_blank">Vue CLI 3</a>
			</li>
			<li>
				<a href="https://stackblitz.com/" target="_blank">Stackblitz</a>
			</li>
			<li>
				<a href="https://github.com/mandril888" target="_blank">GitHub</a>
			</li>
		</ul>

		<div class="h-50"></div>

		<div v-if="!infoFromTest">
			LOADING ...
		</div>

		<div id="PSI-info" v-if="infoFromTest">
			<p><b>Web:</b> {{ infoFromTest.id }}</p>
			<p>
				<b>CLS:</b>
				{{
          infoFromTest.lighthouseResult.audits.metrics.details.items[0].cumulativeLayoutShift.toFixed(2)
        }}
			</p>
			<p>
				<b>LCP:</b>
				{{
          infoFromTest.lighthouseResult.audits.metrics.details.items[0].largestContentfulPaint / (60*3)
        }}
			</p>
			<p>
				<b>FID:</b>
				{{
          infoFromTest.lighthouseResult.audits.metrics.details.items[0].maxPotentialFID
        }} ms
			</p>
		</div>
    
	</div>
</template>

<script>
	import axios from "axios";

export default {
  name: "psi",
  data() {
    return {
      infoFromTest: null
    };
  },
  created() {
    const psiApiUrl =
      "https://pagespeedonline.googleapis.com/pagespeedonline/v5/runPagespeed?url=https://seocom.agency";

    axios.get(psiApiUrl).then(response => (this.infoFromTest = response.data));
  }
};
</script>

<style scoped>
	#PSI-info {
		text-align: left;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	#PSI-info li {
		text-align: left !important;
	}

	.psi li {
		text-align: center !important;
	}

	a {
		color: #42b983;
	}

	span {
		color: red;
	}
</style>