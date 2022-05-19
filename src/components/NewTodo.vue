<template>
  <form @submit.prevent="addTodo()" class="col-12 p-0 mb-1">
    <input v-model="newTodo" placeholder="Enter Todo" type="text" class="form-control" />
  </form>
</template>

<script>
export default {
  data() {
    return {
      newTodo: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length > 1) {
        this.$emit("on-addtodo", this.newTodo);
      }
      this.newTodo = "";
    }
  }
};
</script>

<style lang="stylus" scoped></style>