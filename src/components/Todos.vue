<template>
  <div>
    <div  v-for="todo in todos" v-bind:key="todo.guid">
      <TodoItem v-bind:todo="todo" @del-todo="$emit('del-todo', todo.guid)"  @check-comment="checkComment(todo.guid)" @add-comment="addComment(todo.guid)" class="accordion" />
      <div class="panel" v-if="flagAddComment && (idHolder == todo.guid)" id="commentForm">
        <form @submit.prevent="addCommentForm">
          <input class="inpt" type="text" v-model="by" name="title" placeholder="Enter by...">
          <input class="inpt" type="text" v-model="comment" name="title" placeholder="Enter comment...">
          <input class="inpt" type="date" v-model="date" name="title" placeholder="Select date...">

          <input type="submit" value="Save" class="btn">
        </form>
      </div>
      <div class="panel" v-if="flagComment && (idHolder == todo.guid)">
        <table>
          <tr>
          <th style="width:10%; text-align:left">By</th>
          <th style="width:50%; text-align:left">Comment</th>
          <th style="width:10%; text-align:left">Date</th>
          <th style="width:20%; text-align:right">Action</th>
        </tr>
        <tr v-for="(comment, index) in todo.comments" :key="index">
          <td style="width:10%" >{{ comment.by }}</td>
          <td style="width:50%" >{{ comment.comment }}</td>
          <td style="width: 10%">{{ comment.date }}</td>
          <td style="width:20%" >
            <small class="update">Update</small>
            <small class="del" @click="$emit('del-comment', todo.guid, index)">X</small>
          </td>
        </tr>
        </table>
      </div>
    </div>
  </div>
</template>

<script >
import TodoItem from './TodoItem.vue';

export default {
  name: "Todos",
  components: {
    TodoItem
  },
  data() {
    return {
      flagComment: false,
      flagAddComment: false,
      idHolder: '',
      by: '',
      comment: '',
      date: ''
    }
  },
  props: ["todos"],
  methods: {
    checkComment(id) {
      this.idHolder = id;
        if(!this.flagComment) { //toggle
          this.flagComment = true;
        } else {
          this.flagComment = false;
        }
    },
    addComment(id) {
      this.idHolder = id;
      if(!this.flagAddComment) { //toggle
          this.flagAddComment = true;
        } else {
          this.flagAddComment = false;
        }
    },
    addCommentForm() {
      const newComment = {
        by: this.by,
        comment: this.comment,
        date: this.date
      }

      // Send up to parent
      this.$emit('add-comment', newComment, this.idHolder);

      this.reset(); // reset field after adding
    },
    reset() {
      this.by = '';
      this.comment = '';
      this.date = '';
    }
  }
}
</script>

<style scoped>


#commentForm {
  text-align: center;
  margin-top: 5px;
  margin-bottom: 5px;
}
.btn {
  margin-left: 5px;
}
.inpt {
  padding: 5px;
  margin-left: 5px;
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
.accordion {
  background-color: #eee;
  color: #444;
  cursor: pointer;
  padding: 18px;
  width: 100%;
  border: none;
  text-align: left;
  outline: none;
  font-size: 15px;
  transition: 0.4s;
}

.active, .accordion:hover {
  background-color: #ccc; 
}

/* .panel {
  padding: 0 18px;
  display: none;
  background-color: white;
  overflow: hidden;
} */
</style>

