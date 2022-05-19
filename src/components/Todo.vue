<template>
  <li class="d-flex align-items-center list-group-item p-2">
    <button
      v-if="!isEditing"
      :class="completed?'completed':''"
      @click="toggleTodo()"
      class="btn border-0 text-left flex-grow-1"
    >{{todoString}}</button>
    <form v-else @submit.prevent="endEditing()" class="flex-grow-1">
      <input @blur="startEditing()" v-model="newTodoString" type="text" class="form-control" />
    </form>
    <button @click="startEditing()" class="btn btn-outline-primary mx-2">
      <i class="fa fa-pencil-alt"></i>
    </button>
    <button @click="$emit('on-delete')" class="btn btn-outline-danger">
      <i class="fa fa-trash-alt"></i>
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todoString: String,
    completed: Boolean
  },
  data() {
    return {
      newCompleted:false,
      isEditing: false,
      newTodoString: ""
    };
  },
  methods: {
    startEditing() {
      // console.log("start editing");
      if (!this.isEditing) {
        this.newTodoString = this.todoString;
        this.isEditing = true;
      } else {
        this.endEditing();
      }
    },
    endEditing() {
      // console.log("end editing");
      // console.log(this);
      this.isEditing = false;
      this.$emit("on-edit", this.newTodoString);
    },
    //taken from parent to child
    toggleTodo() {
      this.completed=!this.completed;
      // console.log(a);
    }
  }
};
</script>


<style scoped>
.completed {
  text-decoration: line-through;
}
</style>