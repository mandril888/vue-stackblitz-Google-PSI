<template>
  <div class="psi">
    <div id="PSI-info" v-if="infoFromTest">
      <p>Web: {{ infoFromTest.id }}</p>
      <p>
        CLS:
        {{
          infoFromTest.lighthouseResult.audits.metrics.details.items[0].cumulativeLayoutShift
        }}
      </p>
      <p>
        LCP:
        {{
          infoFromTest.lighthouseResult.audits.metrics.details.items[0].largestContentfulPaint
        }}
      </p>
      <p>
        FID:
        {{
          infoFromTest.lighthouseResult.audits.metrics.details.items[0].maxPotentialFID
        }} ms
      </p>
      <div class="h-100"></div>
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
