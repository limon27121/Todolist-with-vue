<template>
    <div class="container">
      <div class="task">
        <!-- title -->
        <div class="title">
          <h1>To Do List</h1>
        </div>
        <!-- form -->
        <div class="form">
          <input type="text" placeholder="New Task" v-model="Newtask" @keyup.enter="addtask"/>
          <button @click="addtask()"><i class="fas fa-plus"></i></button>
        </div>
        <!-- task lists -->
        <div class="taskItems">
          <ul>
            <li v-for="task in tasks" :key="task.id">
              <span class="circle-icon" @click="toggleTaskStatus(task)">
      <i :class="{ 'far fa-circle': !task.completed, 'fas fa-check-circle':task.completed }"></i>
    </span>
              
                <span :class="classname(task)">{{ task.title }}</span>
              <button @click="deleteTask(task)"><i class="far fa-trash-alt"></i></button>
            </li>
           
          </ul>
        </div>
        <!-- buttons -->
        <div class="clearBtns">
          <button @click="clear">Clear completed</button>
          <button @click="clearall">Clear all</button>
        </div>
        <!-- pending task -->
        <div class="pendingTasks">
          <span>Pending Tasks:{{ incomplete }} </span>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "Task",
    // props:["tasks"],

    
    computed:{
      //find the inprogress work length
     incomplete(){
      return this.tasks.filter(this.isprogress).length
     },

    //  classname() {
    //   return (task) => {
    //     let cls = ["toggle"];
    //     if (task.completed) {
    //       cls.push("toggle-completed");
    //     }
    //     return cls;
    //   };
    // },

    },
    data(){
      return{
        Newtask:"",
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
      addtask() {
        if (this.Newtask.length > 0) {
            this.tasks.push({
              title: this.Newtask, // Use this.Newtask to access the data property
              completed: false,
              });
          
      this.Newtask = ""; // Clear the input after adding the 
    }
   else{
    alert("invalid input")
   }
    
  },
      clearall(){
        this.tasks=[]
      },
      //which work are not done
      isprogress(task){
        return !this.iscompleted(task)
      },
      //which work is done
      iscompleted(task){
          return task.completed;
      },

    // clear(){
    //   // this.tasks= this.tasks.filter(this.isprogress)
    //   this.tasks=this.tasks.filter(()=>{
    //     this.task.completed=="false"
    //   })
    // }

  clear() {
  this.tasks = this.tasks.filter((task) => !task.completed);
},

deleteTask(task){
  const index = this.tasks.indexOf(task);
    if (index !== -1) {
      this.tasks.splice(index, 1);
    }
},

toggleTaskStatus(task) {
      task.completed = !task.completed;
    },


//line through style acitivated 
    classname(task) {
      let cls = ["toggle"];
      if (task.completed) {
        cls.push("toggle-completed");
      }
      return cls;
    }
    }
  };
  </script>
  