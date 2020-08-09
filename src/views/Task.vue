<template>
    <div>
        <div v-for="task in tasks" :key="task._id">
            <p> {{ task.content }} </p> 
        <button>eliminar</button>
        <button>actualizar</button>
        </div>
    </div>
</template>

<script>
import axios from 'axios';
    export default {
        data() {
            return {
                tasks: []
            }
        },
        async mounted () {
            let url = "https://academlo-todolist.herokuapp.com/tasks"
            const res = await axios.get(url)
            // console.log(res.data.results)
            this.tasks = res.data.results
        },
    }
</script>

<style lang="scss" scoped>

</style>