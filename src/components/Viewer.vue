<script>
 import { loadMathJax, createTooltips } from 'http://localhost:8000/static/tooltips.js'
 import { setupClassInteractions } from 'http://localhost:8000/static/classes.js'

 export default {
     props: ['body'],

     updated() {
         setupClassInteractions();
         loadMathJax();
         createTooltips();
     }
 }
</script>


<template>
  <div class="viewer">
    <div class="mount-manuscript-here" v-html="body">
    </div>
  </div>
</template>


<style>
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
