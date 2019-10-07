<template>
  <div class="todo-item" v-bind:class="{'is-complete': todo.completed}">
    <input type="checkbox" v-on:change="markComplete" v-bind:checked="todo.completed" />
    <p v-if="test !== todo.id">
      {{todo.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">
        <font-awesome-icon icon="trash" />
      </button>
      <button class="edit-btn" @click="editTodo(todo.id)">
        <font-awesome-icon icon="pencil-alt" />
      </button>
    </p>
    <p v-else>
      <input type="text" v-model="todo.title" />
      <button class="cancel-btn" @click="cancelEdit()">
        Cancel
      </button>
      <button class="save-btn" @click="saveData">
        Save
      </button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data() {
    return {
      test: null
    };
  },
  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
    editTodo(id) {
      this.test = id;
    },
    cancelEdit() {
      this.test = null;
    },
    saveData(e) {
      e.preventDefault();
      this.$emit('saveData', this.todo);
      this.test = null;
    }
  }
};
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

.del,
.edit-btn,
.save-btn,
.cancel-btn {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  cursor: pointer;
  float: right;
  margin: 5px;
}

.edit-btn {
  background: rgb(158, 158, 49);
}

.save-btn {
  background: rgb(93, 148, 12);
}

.cancel-btn {
  background: #ff0000; 
}
</style>