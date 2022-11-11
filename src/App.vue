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
             this.body = value;
         }
     },
     components: {
         Viewer, Editor
     }
 }
</script>

<template>
  <div class="body">
    <Editor :value="body" @make="display"/>
    <Viewer :body="body" />
  </div>
</template>

<style lang="scss">
 @import './assets/base.css';
 @import './assets/rsm.scss';
</style>
