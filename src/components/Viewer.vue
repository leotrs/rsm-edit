<script>
 import { onload } from 'https://rsm-api.fly.dev/static/onload.js'

 export default {
     props: ['body'],

     updated() {
         onload();
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
 @import 'https://rsm-api.fly.dev/static/rsm.css';
 @import 'tooltipster/dist/css/tooltipster.bundle.css';

 .viewer {
     height: 100%;
     overflow-y: scroll;
     width: 50%;
 }

 .mount-manuscript-here {
     width: 100%;
 }

 .mount-manuscript-here section.level-1 {
     margin-top: 1rem;
 }

 .mount-manuscript-here .manuscriptwrapper {
     margin-top: 0;
     padding-inline: 3rem;
     box-shadow: unset;
     background: white;
     border-radius: 0;
 }


</style>
