<template>
  <div @click="xyz">
    <h1>Keval</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "./components/TodoList.vue";
export default {
  // name: "App",
  components: {
    TodoList
  },
  methods: {
    xyz(){
      console.log("hello");
    }
  },
};
</script>


<style >
body {
  background-color: rgb(66, 66, 66);
  color: aliceblue;
}
.btn:focus{
  box-shadow: none !important;
}
</style>