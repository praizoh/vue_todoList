<template>
  <div id="app">
    <div class="row">
      <!-- todos -->
      <div class="col">
        <h3>Tasks</h3>
        <h3>Deadline</h3>
        <h3>Assigned To:</h3>
        <h3>Priority</h3>
        <h3>Difficulty</h3>
      </div>
      <form>
      <label for="text"> Enter task here: </label>
      <input type="text" id="text" v-model="test" required/>
      <label for="dLine">Deadline:</label>
      <input type="date" id="dLine" v-model="date" required/>
      <label for="actor">Assigned To:</label>
      <input type="text" v-model="actor" required/>
      <select v-model="priority">
        <option disabled value="">Priority</option>
        <option>Less Important</option>
        <option>Important</option>
        <option>More Important</option>
      </select>
      <select v-model="difficulty">
        <option disabled value="">Difficulty</option>
        <option>Low</option>
        <option>Medium</option>
        <option>High</option>
      </select>

      <button v-on:click="addItem"> Add To Do Here... </button>

      </form>
    </div>
    <br/><br/>
    <table id="firstTable">
      <thead>
        <tr>
          <th>ID</th>
          <th>Tasks</th>
          <th>Date</th>
          <th>Assigned To:</th>
          <th>Priority</th>
          <th>Difficulty</th>
          <th>Completed</th>
          <th>Delete</th>


        </tr>
      </thead>
      <tbody>
        <tr v-for="todo in todos" v-bind:title="message">
          <td>{{todo.id}}</td>
          <td>{{todo.text}}</td>
          <td>{{todo.date}}</td>
          <td>{{todo.actor}}</td>
          <td>{{todo.priority}}</td>
          <td>{{todo.difficulty}}</td>
          <td>
            <input type="checkbox" v-if="todo.completed" checked />
            <input type="checkbox" v-else=""/>
          </td>
          <td> <button v-on:click="delItem(todo.id)">x</button></td>
        </tr>
      </tbody>
    </table>

  </div>
</template>

<script>

export default {
  name: 'app',
  components: {
    // Todos
  },
  
  data() {
    return {
      todos: [
        {id:1, text:'cook food', date:'05/05/2019', actor:'praise', completed:true, priority:'important', difficulty:'high'},
        {id:2, text:'build house', date:'05/05/1990', actor:'Seyi', completed:false, priority:'More Important', difficulty:'low'}
      ],
    
    test: '',
    date:'',
    actor:'',
    priority: '',
    message:'You added this todo item on ' +  new Date().toLocaleString(),

    }   
  },
  methods: {
    addItem(e){
    e.preventDefault();
    // if(this.test!=="" && this.actor!=="" && this.date!==""){
      const newTodo = {
    text: this.test,
    date:this.date,
    actor:this.actor,
    completed:false,
    priority: this.priority,
    difficulty:this.difficulty,
    id:this.todos.length + 1
    }
    this.todos.push(newTodo)
    this.test=''
    // }
        
    },
    delItem(id){
       this.todos=this.todos.filter(todo => todo.id !==id);
    },
  
  } 
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: left; */
  color:white;
  margin-top: 60px;
  background: red;
}
form{
  display: flex;
  justify-content:space-evenly;
}
.col{
  display: flex;
  justify-content:space-evenly;
}
/* style for tables */
table {
  font-family: 'Open Sans', sans-serif;
  width: 95%;
  border-collapse: collapse;
  border: 3px solid #44475C;
  margin: 10px 10px 0 10px;
}

table th {
  text-transform: uppercase;
  text-align: left;
  background: #44475C;
  color: #FFF;
  padding: 8px;
  min-width: 30px;
}

table td {
  text-align: left;
  padding: 8px;
  border-right: 2px solid #7D82A8;
  text-transform: uppercase;
}
table td:last-child {
  border-right: none;
}
table tbody tr:nth-child(2n) td {
  background: #44475C;
  color:white;
}
 
</style>
