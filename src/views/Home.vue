<template>
  <div id="app">
    <AddTodo v-on:add-todo="addTodo" />
    <div class="pagination">
      <a href="#" v-if="page != 1" @click="page--">Previous</a>
      <a href="#" >{{ page }}</a>
      <a href="#" @click="page++" v-if="page < todos.length">Next</a>

    </div>
    <Todos v-bind:todos="todos" @del-todo="deleteTodo" @del-comment="deleteComment" @add-comment="addComment"/>

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
      todos: [],
      todoLen: '',
      page: 1,
			perPage: 20,
      start: 0,
      end: 4,
    }
  },
  mounted() {
    this.getAllTodo();
  },
  filters: {
		paginate: function(array, start, end) {
			return array.slice(start, end);
    }
  },
  methods: {
    // eslint-disable-next-line
    /* eslint-disable */
    paginate: function(direction) {
			if(direction === 'moveRight') 
      {
        if(this.end >= this.images.length) {
          this.start = this.start
          this.end = this.images.length
        } else {
				    this.start += 1;
				    this.end += 1;          
        }
			}
			else if(direction === 'previous') {
        if(this.start <= 0) {
          this.start = 0;
          this.end = 4;
        } else {
				    this.start -= 1;
				    this.end -= 1;
        }
			}
		},
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.guid !== id);
    },

    nextPage(pge) {
      alert(pge);
      this.page += 1;
      // if(page != pge) {

      // }
    },

    deleteComment(id, idx) {
      console.log("todoComment data", id, idx); // check todos id and comment index
      let tmp = this.todos.filter(todo => todo.guid === id);
      let cmmnt = tmp[0].comments;
      let rem = cmmnt.splice(idx, 1); // remove comment
    },

    addComment(comment, tId) {
      console.log("check new comment", comment);
      let tmp = this.todos.filter(todo => todo.guid === tId);
      let cmmnt = tmp[0].comments;
      let add = cmmnt.unshift(comment);
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
          this.todoLen = response.data.topics.length;
          this.todos.length = 20;
          
          console.log("check todo len", this.todoLen);
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
    padding:100px 300px 0 300px;
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

  .pagination {
    display: inline-block;
  }

  .pagination a {
    color: black;
    float: left;
    padding: 8px 16px;
    text-decoration: none;
  }

</style>
