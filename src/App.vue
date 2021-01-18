<template>
  <div id="app">
    <Header @show-form = "show"
            :changeText = "showForm"/>
    <Content :showForm = "showForm"
            @add-book = "show"/>
    
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Content from './components/Content.vue'


export default {
  name: 'App',
  components: {
    Header,
    Content
  },
  data(){
    return{
      showForm: false,
    }
  },
  methods:{
    show: function(value){
      this.showForm = value;
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
