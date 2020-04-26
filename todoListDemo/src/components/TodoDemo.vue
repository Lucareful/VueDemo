<template>
  <div id="todoList">
    <h1>Todo List</h1>
    <todo-add v-on:add="addTodo"></todo-add>
    <input type="checkbox" name value :checked="todo.isCompleted" @click="completed(index)" />
    <span :class="todo.isCompleted ? 'completed' : '' " @click="completed(index)"></span>
    <ul class="todos">
      <li v-for="todo, index in todos" class="todo">
        <em>{{ index }}.</em>
        {{ todo.text }}
      </li>
    </ul>
  </div>
</template>
<script>
// 引入子组件
import TodoAdd from "./TodoAdd.vue";
export default {
  name: "TodoList",
  components: {
    TodoAdd
  },
  data: () => ({
    todos: [
      {
        text: "学习",
        isCompleted: false
      }
    ]
  }),
  methods: {
    completed(index) {
      this.todos[index].isCompleted = !this.todos[index].isCompleted;
    },
    addTodo() {
      this.todos.push({
        text: todo,
        isCompleted: false
      });
    }
  }
};
</script>
<style scoped>
#todoList {
  margin: 0 auto;
  max-width: 350px;
}
.todos li {
  list-style: none;
}
.todo {
  text-align: left;
  cursor: pointer;
}
.completed {
  text-decoration: line-through;
}
</style>