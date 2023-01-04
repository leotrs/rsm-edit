<script>
 export default {
     data() {
         let params = new URLSearchParams(document.location.search);
         let src = params.get("src");
         if (src === null || src === "") src = ":manuscript:\n  :title: Hello, RSM!\n\n# What is this?\n\nReStructured Manuscripts (RSM) is a set of tools for building web-first scientific manuscripts.  At the core of the RSM system lies the RSM markup language.  The text you see to your left is in RSM markup.\n\nWriting RSM markup instead of LaTeX, Markdown, or ReST allows you to focus on your manuscript's content and leave the layout, styles, and display to RSM.\n\n::\n\n# Features\n\n## Handrail\n\nOn the left-hand side of every heading you will see a gray border that we call /the handrail/.  The handrail shows a context menu for that specific part of the manuscript.  Many other parts of the manuscript have handrails\\:\n\n:remark:\n  :label: rmk\n\nThis is a remark, and it has a handrail.\n\n::\n\n::\n\n## Tooltips\n\nAny part of the manuscript can be referenced.  For example, :ref:rmk,this:: refers to the remark above.  If you hover over the link text, you will see a tooltip showing the referenced part.\n\n::\n\n## Bibliography\n\nRSM accepts bibliography items in BibTex syntax.  Here are a few examples :cite:knuth,turing::.  Note you can hover on the citation number to see the reference without scrolling the page. The reference list at the bottom has backlinks over which you can also hover, as well as links to DOI URLs, if available.\n\n::\n\n::\n\n# More!\n\nSee :url:https://docs.write-rsm.org, the documentation:: to learn more about RSM.\n\n::\n\n:bibliography: ::\n\n::\n\n\n:bibtex:\n\n@book{knuth,\n  title={Art of computer programming, Volume 2, Seminumerical algorithms},\n  author={Knuth, Donald E},\n  year={2014},\n  publisher={Addison-Wesley Professional},\n  doi = {10.1137/1012065},\n}\n\n@article{turing,\n  author = {Turing, Alan M},\n  title = {Computing machinery and intelligence},\n  journal = {Mind},\n  year = {1950},\n  doi = {10.1093/mind/LIX.236.433},\n}\n\n::\n"

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
