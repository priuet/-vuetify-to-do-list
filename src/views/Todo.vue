<template>
  <div class="home">
        <h1 class="pa-10">Todo Page</h1>

    <v-text-field  
        v-model="newTaskTitle"
        @click:append='addTask'
        @keyup.enter='addTask'
        class="pa-5"
        solo 
        hide-details
        clearable
        label="Add Task"
        append-icon="mdi-plus"
    ></v-text-field>

    <v-list class="pt-0"
      two-line
      subheader
    >
    <div   
        v-for="task in tasks"
        :key="task.id"
    >
    
    <v-list-item @click = 'doneTask(task.id)'
      :class= "{ 'green lighten-5' : task.done }">

        <template v-slot:default>
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

        <v-list-item-content>
            <v-list-item-title 
              :class="{ 'text-decoration-line-through' : task.done }"
            >
            {{ task.title }}</v-list-item-title>
        </v-list-item-content>

        <v-list-item-action>
          <v-btn icon
          @click.stop="deleteTask(task.id)">
            <v-icon color="primary lighten-1">mdi-delete</v-icon>
          </v-btn>
        </v-list-item-action>

          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>

</div> 
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      newTaskTitle: '',
      tasks: [
        {
        id: 1,
        title: 'brush teeth',
        done: false
        },
        {
        id: 2,
        title:'buy purple socks',
        done: false
        },
        {
          id: 3,
          title: 'upload videos to Youtube',
          done: false
        }
      ]
    }
  },
  methods: {
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false
      }
      this.tasks.push(newTask)
      this.newTaskTitle = ''
    },
    doneTask(id) {
      let task = this.task.filter(task => task.id === id)[0]
      task.done = !task.done
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }
}
</script>
