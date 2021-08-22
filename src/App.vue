<template>
  <div id="app">
    <h1>Hyperstructurization</h1>
    <text-node :nodedata='flare'></text-node>
  </div>
</template>

<script>
import TextNode from './components/TextNode.vue';

export default {
  name: 'App',
  components: {
    TextNode
  },
  data: function() {
    return { flare: { content: "", children: []} }
  },
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.mr-1 {
  margin-right: 1rem;
}

</style>
