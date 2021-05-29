<template>
    <div class="p-3">
        <div class="d-flex justify-content-center">
            <button :class="{'focus': task==0, 'bg-danger': showFormTask}" @click="create_task" class="btn border btn-success px-4 py-2">
                {{ showFormTask? 'Cerrar':'Crear Apunte'}}
            </button>
        </div>    
        <div v-show="showFormTask" class="mt-3">
            <form action="#">
                <div class="form-group">
                    <label for="title">Title</label>
                    <input autocomplete="off" id="addTitleInput" type="text" v-model="title" class="form-control">
                </div>
                <div class="form-group">
                    <button :disabled="!title" class="btn border btn-primary" @click.prevent='addNewTask'>Guardar</button>
                </div>
            </form>            
        </div>
    </div>
</template>

<script>
export default {
    name: "Create",
    props: {
        task: Array,
        showFormTask: Boolean
    },
    data(){
        return {
            title: ''
        }
    },
    methods: {
       addNewTask(){
           this.$emit("addNewTask", this.title)
           this.title = ''
       },
       create_task(){
           this.$emit("create_task")
           setTimeout(()=>{
               document.querySelector("#addTitleInput").focus()
           }, 100)
       }
    },
    setup() {
        
    },
}
</script>