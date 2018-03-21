<template>
  <div class="reveal">
    <div class="slides">
      <section>Slide 11</section>
      <section>Slide 2</section>
      <section>Slide 3</section>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'HelloWorld',
    data () {
      return {
        msg: 'Welcome to Your Vue.js App'
      }
    },
    mounted(){
      Reveal.initialize({
        dependencies: [
          { src: './static/reveal/plugin/markdown/marked.js' },
          { src: './static/reveal/plugin/markdown/markdown.js' },
          { src: './static/reveal/plugin/notes/notes.js', async: true },
          { src: './static/reveal/plugin/highlight/highlight.js', async: true, callback: function() { hljs.initHighlightingOnLoad(); } }
        ]
      });
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="less" scoped>
  /*@import "HelloWorld.less";*/
</style>
