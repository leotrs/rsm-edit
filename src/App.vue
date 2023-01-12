<script>
 import Editor from './components/Editor.vue'
 import Viewer from './components/Viewer.vue'


 export default {
     data() {
         return {
             body: ""
         }
     },
     methods: {
         display(value) {
             value = value.replace(/class="manuscriptwrapper"/, 'class="manuscriptwrapper embedded"');
             this.body = value;
         }
     },
     components: {
         Viewer, Editor
     }
 }
</script>


<template>

  <header class="nav">
    <input id="the-menu" type="checkbox"/>
    <label id="the-label" for="the-menu"></label>
    <nav class="nav-row nav-main">
      <span class="links">
        <span class="link-wrapper no-border"><a class="logo" href="https://www.write-rsm.org/"><strong>:rsm:</strong></a></span>
        <span class="link-wrapper"><a href="https://docs.write-rsm.org/en/latest/tutorials/markup.html">Tour</a></span>
        <span class="link-wrapper"><a href="https://docs.write-rsm.org/en/latest/tutorials.html">Getting Started</a></span>
        <span class="link-wrapper"><a href="https://docs.write-rsm.org/en/latest/contributing.html">Contribute</a></span>
        <span class="link-wrapper"><a href="https://docs.write-rsm.org/">Docs</a></span>
      </span>
      <span class="socials">
        <a class="twitter" href="https://twitter.com/write_rsm"></a>
        <a class="youtube" href=""></a>
        <a class="github" href="https://github.com/leotrs/rsm"></a>
      </span>
    </nav>
  </header>

  <div class="body">
    <Editor :value="body" @make="display"/>
    <Viewer :body="body" />
  </div>

  <footer class="footer">
    <div class="footer-wrapper">
      <a class="logo logo-light" href="https://www.write-rsm.org/"><strong>:rsm:</strong></a>
      <p style="margin:0">Made with <span class="heart">❤</span> by leotrs</p>
      <span class="socials">
        <a class="twitter-light" href="https://twitter.com/write_rsm"></a>
        <a class="youtube-light" href=""></a>
        <a class="github-light" href="https://github.com/leotrs/rsm"></a>
      </span>
    </div>
  </footer>

</template>


<style lang="scss">
 @import 'https://www.write-rsm.org/static/index.css';

 #app {
     max-width: 1280px;
     margin: 0 auto;
     font-weight: normal;
     height: 100%;
     width: 100%;
     position: absolute;
 }

 .body {
     display: flex;
     gap: 1.5%;
     width: 100%;
     height: 77%;
     margin-block: 2rem;
 }

</style>
