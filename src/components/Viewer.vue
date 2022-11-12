<script>
 import "https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"
 import { loadTooltips } from 'http://localhost:8000/static/tooltips.js'

 export default {
     props: ['body'],
     updated() {
         loadTooltips();
     }
 }
</script>


<template>
  <div class="viewer">
    <div class="mount-manuscript-here" v-html="body">

    </div>
  </div>
</template>


<style lang ="scss">
 @import 'http://localhost:8000/static/rsm.css';
 @import 'tooltipster/dist/css/tooltipster.bundle.css';

 .viewer {
     height: 100%;
     width: 50%;
 }

 .mount-manuscript-here {
     height: 100%;
     width: 100%;
 }

</style>
