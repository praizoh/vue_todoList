<template>
  <div id="app">
    <ol>
      <li v-for="todo in todos">
        
      </li>
    </ol>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Todos from './components/Todos'

export default {
  name: 'app',
  components: {
    // Todos
  },
  data() {
    return {
      todos: [
      { id:1, text: 'Learn JavaScript', completed:false },
      { id:2, text: 'Learn Vue', completed:false },
      { id:3, text: 'Build something awesome', completed:true }
    ]
    }   
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
