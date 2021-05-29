<template>
    <header class="p-3">
        <h2 class="display-3 text-center m-5">Mis Apuntes</h2>
        <Create @addNewTask="addNewTask" :showFormTask="showFormTask" :task="task" @create_task="create_task" />
    </header>
</template>

<script>
import Create from './Create'
export default {
    name: "Header",
    props: {
        task: Array,
        showFormTask: Boolean
    },
    components: {
        Create
    },
    methods:{
        addNewTask(e){
            this.$emit("addNewTask", e)
        },
        create_task(){
            this.$emit("create_task")
        }
    },
    setup() {
        
    },
}
</script>