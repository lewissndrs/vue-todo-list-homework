<template>
  <div id="app">
    <h1>To Do's</h1>

    <form v-on:submit.prevent="addToList">
      <label for="name">Name</label>
      <input type="text" id='name' v-model="newItem">
      
      <label for="priority">Priority: </label>
      <input type="radio" name='priority' value='high' v-model="priorityTrack">
      <label for="high">High</label>
      <input type="radio" name='priority' value='low' v-model="priorityTrack">
      <label for="low">Low</label>

      <input type="submit" id="submit">
    </form>

    <ul>
      <li v-for="(todo, index) in todos" :key="index" v-bind:class="todo.hiPriority ? 'hi' : 'lo'">
        <span>{{ todo.name }}</span>
        </li>
    </ul>

  </div>
</template>

<script>
export default {
  data(){
    return {
      todos : [{name:"Buy a parrot",hiPriority:false},{name:"Love oneself",hiPriority:true},{name:"clean potatoes",hiPriority:false}],
      newItem : "",
      priorityTrack: ""
    }
  },
  methods: {
    addToList: function() {

      let priority = null;

        if (this.priorityTrack === "high") {
          priority = true;
        } else {
          priority = false;
        };

      this.todos.push({
        name:this.newItem,
        hiPriority:priority
        });
      this.newItem = "";
      this.priorityTrack = "";
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
  font-size: 25px;
}

form {
  text-align: start;
  width: 55%;
  margin: auto;
}

form > input, form > label {
  padding: 5px;
  margin: 5px;
  font-size: 25px;
}

#submit {
  background-color: black;
  color: white;
  font-size: 25px;
  border-radius: 0;
  padding: 5px;
}

li {
  list-style-type: none;
  padding: 10px;
  text-align: start;
  width: 60%;
  margin: 12px auto;
}

li > span {
  padding-left: 3%;
}

.hi {
  color: red;
  border: 2px solid red;
}

.lo {
  color: dodgerblue;
  border: 2px solid dodgerblue;
}
</style>


