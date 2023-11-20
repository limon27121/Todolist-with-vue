<template>
    <div class="container">
      <div class="task">
        <!-- title -->
        <div class="title">
          <h1>To Do List</h1>
        </div>
        <!-- form -->
        <div class="form">
          <input type="text" placeholder="New Task" v-model="task"/>
          <button @click="addtask()"><i class="fas fa-plus"></i></button>
        </div>
        <!-- task lists -->
        <div class="taskItems">
          <ul>
            <li v-for="task in tasks" :key="task.id">
              <button>
                {{ task.title }}</button>
              <button><i class="far fa-trash-alt"></i></button>
            </li>
           
          </ul>
        </div>
        <!-- buttons -->
        <div class="clearBtns">
          <button>Clear completed</button>
          <button @click="clearall">Clear all</button>
        </div>
        <!-- pending task -->
        <div class="pendingTasks">
          <span>Pending Tasks: </span>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "Task",
    // props:["tasks"],
    data(){
      return{
        task:"",
        tasks: [
        {
          id: 1,
          title: "Learn Vue JS",
          completed: true,
        },
        {
          id: 2,
          title: "Watch netflix",
          completed: true,
        },
        {
          id: 3,
          title: "Go shopping",
          completed: false,
        },
        {
          id: 4,
          title: "Learn guitar",
          completed: false,
        },
        {
          id: 5,
          title: "Send email",
          completed: false,
        },
      ],
      }
    },
    methods:{
      clearall(){
        this.tasks=[]
      }
    }
  };
  </script>
  