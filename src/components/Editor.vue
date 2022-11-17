<script>
 export default {
     data() {
         return {
             value: ":manuscript:\n  :title: Some title\n\n# Tooltips\n\nOne of the main features of RSM is that anything can be labeled and referenced.  For\nexample,\n\n:theorem:\n   :label: some-thm\n\n   :paragraph: {:label: some-stm} All $X$ are $Y$.\n\n   And this is another paragraph.\n\n::\n\nThe first paragraph of the theorem has been labeled and can now be referred to\n:ref:some-stm,like this::.  The entire theorem itself can be referred to\n:ref:some-thm,like this:: (**NOTE\\: ** sometimes the math in the tooltip is displayed\nincorrectly.  If the tooltip does not show, refresh the page a few times first.)\n\nNote the Theorem block also has a handrail and will eventually support a more\nfully-featured context menu.\n\n::\n\n::\n"
         }
     },
     methods: {
         make(event) {
             console.log('emitting make event');

             fetch('http://localhost:8000/make', {
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
    <button @click="make">Make!</button>
  </div>
</template>

<style scoped>
 .editor {
     height: 100%;
     width: 50%;
 }

 #input {
     height: 100%;
     width: 100%;
 }
</style>
