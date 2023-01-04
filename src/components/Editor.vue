<script>
 export default {
     data() {
         let params = new URLSearchParams(document.location.search);
         let src = params.get("src");
         if (src === null || src === "") src = ":manuscript:\n  :title: Some title\n\n# Tooltips\n\nOne of the main features of RSM is that anything can be labeled and referenced.  For example,\n\n:theorem:\n   :label: some-thm\n\n   :paragraph: {:label: some-stm} All $X$ are $Y$.\n\n   And this is another paragraph.\n\n::\n\nThe first paragraph of the theorem has been labeled and can now be referred to :ref:some-stm,like this::.  The entire theorem itself can be referred to :ref:some-thm,like this::. \n\nNote the Theorem block also has a handrail and will eventually support a more\nfully-featured context menu.\n\n::\n\n::\n";
         return {
             value: src
         }
     },
     methods: {
         make(event) {
             console.log('emitting make event');

             fetch('https://rsm-api.fly.dev/make', {
	         method: 'PUT',
	         headers:{'Content-Type':'application/json'},
	         body: JSON.stringify({
                     src: this.value
                 })
             }).then(response => {
                 return response.json()
             }).then(data => {
                 this.$emit('make', data.output);
             });
         }
     }
 }
</script>

<template>
  <div class="editor">
    <textarea id="input" v-model="value"/>
    <button id="rsm-make" class="cta" @click="make">Make!</button>
  </div>
</template>

<style scoped>
 .editor {
     height: 100%;
     width: 50%;
     display: flex;
     flex-direction: column;
     align-items: center;
 }

 #input {
     width: 100%;
     height: 100%;
     margin-bottom: 1.5rem;
     font-size: 1rem;
 }

 #rsm-make {
     width: 20%;
     font-size: 1.2rem;
     border: none;
 }

</style>
