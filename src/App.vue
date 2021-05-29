<template>
    <div id="app" class="container">
        <Header @addNewTask="addNewTask" :showFormTask="showFormTask" :task="tasks" @create_task="create_task" />
        <Tasks style="min-height: 45vh" :task="tasks" />
        <Footer />
    </div>
</template>

<script>

import Header from './components/Header'
import Tasks from './components/Tasks'
import Footer from './components/Footer'

export default {
  name: "App",
  data(){
    return {
      showFormTask: false,
      tasks: []
    }
  },
  components: {
    Header,
    Tasks,
    Footer
  },
  methods: {
    addNewTask(e){
      this.tasks.unshift({
        id: Date.now(),
        title: e
      })
      // this.showFormTask = false
    },
    create_task(){
      this.showFormTask = !this.showFormTask
    }
  },
  mounted(){
    var apuntes = [
        {id:1, title: 'Aprender Vue CLI'},
        {id:2, title: 'Aprender Laravel'}
    ]
    this.tasks - apuntes.reverse()
  },
  setup() {
    
  },
}
</script>
 
<style scoped>
    @import url('https://fonts.gstatic.com');
    @import url('https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/css/bootstrap.min.css');
    @import url('https://fonts.googleapis.com/css2?family=Special+Elite&display=swap');
    *{
      font-family: 'Special Elite', cursive;
    }
</style>