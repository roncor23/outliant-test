<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" @del-todo="deleteTodo" />
    
    <!-- <Todos v-bind:todos="todos"/> -->
  </div>
</template>

<script>
import Todos from '../components/Todos';
import AddTodo from '../components/AddTodo';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  mounted() {
    this.getAllTodo();
  },
  methods: {
    // eslint-disable-next-line
    /* eslint-disable */
      
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.guid !== id);
    },

    addTodo(newTodo) {
      console.log("add todo", newTodo);
      this.todos.unshift(newTodo);
    },

    async getAllTodo() {
      try {
        const response = await axios.get('https://atillc.blob.core.windows.net/data-collector/icode/test-data/topics.json')
        .then((response) => {
          this.todos = response.data.topics; 
          
          console.log("check todo", this.todos);
        })
      } catch(error) {
          console.log("err", error);
          alert('Something went wrong!');
      }
    }
  },
  // created() {
  //   // axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
  //   axios.get('https://atillc.blob.core.windows.net/data-collector/icode/test-data/topics.json')
  //     .then(res =>
  //      this.todos = res.data
  //      )
  //     .catch(err => console.log(err));
  // }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }

  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
