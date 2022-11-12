<script>
 export default {
     props: ['body'],
     mounted() {
         const files = ['jquery-3.6.0.js', 'classes.js', 'tooltips.js', 'tooltipster.bundle.js'];
         for (const i in files) {
             const plugin = document.createElement("script");
             plugin.setAttribute(
                 "src",
                 `http://localhost:8000/static/${files[i]}`
             );
             plugin.async = true;
             document.head.appendChild(plugin);
         }
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
 @import 'http://localhost:8000/static/tooltipster.bundle.css';

 .viewer {
     height: 100%;
     width: 50%;
 }

 .mount-manuscript-here {
     height: 100%;
     width: 100%;
 }

</style>
