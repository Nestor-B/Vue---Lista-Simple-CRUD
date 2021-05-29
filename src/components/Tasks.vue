<template>
    <div class="container">
        <div class="lead p-3 d-flex justify-content-end">
            <div v-if="task != 0">
                <strong class="text-success p-1 px-2 rounded-circle border">{{task.length}}</strong> Apuntes Registrados
            </div>
            <div v-else class="container px-4">
                No hay Apuntes
            </div>
        </div>
        <ul class="list-group" v-if="cantidad">
            <li v-for="i, index in task" :key="i.id" class="list-group-item d-flex justify-content-between align-items-center">
                <div>
                    <span class="text-success">{{cantidad.length-index}}</span> - 
                    {{i.title}}
                </div>
                <span class="btn badge badge-pill text-danger border p-2" @click="DeleteItem(i, index)">X</span>
            </li>
        </ul>        
    </div>
</template>

<script>
export default {
    props: {
        task: Array
    },
    methods:{
        DeleteItem(obj, index){
            this.task.splice(index, 1)
        }
    },
    computed:{
        cantidad(){
            return this.task
        }
    },
    setup() {
        
    },
}
</script>