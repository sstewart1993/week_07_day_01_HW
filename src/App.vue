<template>
  <div id="app">
    <ul>
      <li v-for="(todo, index) in todos" v-bind:class="todo.newPriority ? 'high' : 
      'low'" 
      :key="index">
        <span>{{ todo.name }} {{ todo.priority }}</span>
      </li>
    </ul>

    <form v-on:submit.prevent="saveNewTodo">
      <label for="new-todo">Add New Task</label>
      <input type="text" name="new-todo" id="new-todo" v-model="newTodo"/>
      <input type="text" name="new-priority" id="new-priority" v-model="newPriority">
      <input type="submit" value="Save New Task"/>
    </form>

  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      todos: [
      {name: "Buy shopping: ", priority: " high"},
      {name: "Clean bathroom: ", priority: " low"},
      {name:"Car's MOT: ", priority: " Super Duper High"}
      ],      
    newTodo: "",
    newPriority: ""
    }
  },
  methods:{
    saveNewTodo: function(){
      this.todos.push({
        name: this.newTodo,
        priority: this.newPriority

      })
      this.newTodo=""
      this.newPriority=""
    }
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
  margin-top: 60px;
}

body>div>ul>li>span{
  margin: 5px;
  padding: 10px;
  text-transform: capitalize;
}

li.high {
  border: 2px solid #f2360c;
}

li.low {
  border: 2px solid #1a681e;
  color: #1a681e;
}
</style>
