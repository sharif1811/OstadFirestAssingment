<script setup>
    import {ref} from 'vue';
    const tokens = ref([
            { name: "Task-1", time: "1" },
            { name: "Task-2", time: "2" }
        ]);
    function addNewText(){
        const newTask = {
            time: tokens.value.length + 1,
            name: `Task - ${tokens.value.length+ 1}`
        };
        tokens.value.push(newTask);
    }
    function deleteTask(i){
        if(confirm("Are You Sure ?")){
            tokens.value.splice(i, 1);
        }
    }
</script>
<template>
    <table class="table table-bordered">
        <thead>
            <tr>
                <th>Name</th>
                <th>Time</th>
                <th>Acction</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(token,i) in tokens">
                <th>{{ token.name }}</th>
                <td>{{ token.time+" min" }}</td>
                <td>
                    <a href="" @click.prevent="deleteTask(i)" class="btn btn-danger">Remove</a>
                </td>
            </tr>
        </tbody>

    </table>
        <div class="d-grid gap-2 col-6 mx-auto">
            <button @click="addNewText()" class="btn btn-primary" type="button"> New Task</button>
        </div>
</template>
<style scoped>

</style>