<script>
import { onMounted, ref } from 'vue';

const retrieveData = async() =>{
  const response = await fetch("https://jsonplaceholder.typicode.com/todos")
  const data = await response.json()
  return data
}

export default {
     setup() {

        let dataList = ref([])
        let length = ref(0)

        onMounted(async ()=>{
            const data = await retrieveData()
            // data = data.slice(50)
            console.log(data)
            dataList.value = data
            length.value = data.length
        })
        return {
            dataList,
            length
        }
    }
}
</script>

<template>
    <div>Data list length: {{ length }}</div>
    <br>
    <br>
    <div>
        <table>
            <tr>
                <th>Task Name</th>
                <th>Task ID</th>
            </tr>
            <tr v-bind:key='task.id' v-for="(task) in dataList">
                <td>
                {{ task.title }}
                </td>
                <td>
                    {{ task.id }}
                </td>
            </tr>

        </table>
    </div>
    <!-- <table>
        <tr>
            <th>Task name</th>
            <th>Task ID</th>
        </tr>
    <table> -->
</template>

<style scoped>

    .line{
        margin-bottom: 5px;
    }
</style>