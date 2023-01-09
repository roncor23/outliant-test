<template>
  <div class="todo-item">
      {{todo.name}}
      <button @click="$emit('add-comment', todo.guid)" class="add">Add Comment</button>

      <button @click="$emit('check-comment', todo.guid)" class="view">View Comment</button>

      <button @click="$emit('el-todo', todo.guid)" class="update">update</button>

      <button @click="$emit('del-todo', todo.guid)" class="del">x</button>



  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    
  }
}
</script>

<style scoped>
  .todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    margin-left: 20px;
  }
  .update {
    background: #1538fc;
    color: #fff;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    margin-left: 20px;
  }
  .add {
    background: #0bb177;
    color: #fff;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    margin-left: 20px;
  }
  .view {
    background: #c39a06;
    color: #fff;
    border: none;
    padding: 5px 9px;
    cursor: pointer;
    float: right;
    margin-left: 20px;
  }
</style>

