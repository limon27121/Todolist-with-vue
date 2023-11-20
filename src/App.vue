<template>
  <div id="app">
    <Task :tasks="tasks"/>
   
  </div>
</template>

<script>
import Task from "./components/Task";

export default {
  name: "App",
  components: {
    Task
  },
  data() {
    return {
     
    };
  },
};
</script>