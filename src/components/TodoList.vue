<template>
  <div class="container">
    <div class="row">
      <div class="col-12 col-lg-6 mb-2">
        <p class="display-3 text-center"><img src="../assets/logo.png" height="80px"> Vue course</p>
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6 mb-2">
        <NewTodo @on-addtodo="addTodo($event)" />
      </div>
    </div>
    <div class="row">
      <div class="col-12 col-lg-6">
        <ul class="list-group">
          <Todo
            v-for="(todo, index) in todos"
            :key="index"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
            @on-toggle="toggleTodo(todo)"
            @on-edit="editTodo(todo, $event)"
          />
          <Todo
            v-for="(todo, index) in checkedTodos"
            :key="index+todos.length"
            :todoString="todo.todoString"
            :completed="todo.completed"
            @on-delete="deleteTodo(todo)"
            @on-toggle="toggleTodo(todo)"
            @on-edit="editTodo(todo, $event)"
          />
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";
import NewTodo from "./NewTodo";
export default {
  components: {
    Todo,
    NewTodo
  },
  data() {
    return {
      todos: [
        { todoString: "Complete Compliance Training", completed: false },
        { todoString: "typescript and promises", completed: false }
      ],
      checkedTodos:[
        { todoString: "Vue.js crash course", completed: true },
        { todoString: "go through javascript apply bind and call()", completed: true }
      ]
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({
        todoString: newTodo,
        completed: false
      });
    },
    //removed the toggleTodo and added it to child, 
    //moving it from parent to child
    editTodo(todo, newTodoString) {
      todo.todoString = newTodoString;
    },
    deleteTodo(deleteTodo) {
      if(deleteTodo.completed){this.todos = this.todos.filter(todo => todo !== deleteTodo);}
    }
  }
};
</script>


<style >
</style>