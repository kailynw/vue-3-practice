<script>
import { onMounted, ref } from 'vue';

export default {
    async setup() {
        let count = ref(4)

        const incrementCounter = ()=>{
            count.value +=1
        }

        const decrementCounter = ()=>{
            count.value -=1
        }


        onMounted(()=>{
            console.log(count.value)
        })
        return {
            count,
            incrementCounter,
            decrementCounter
        }
    }
}
</script>

<template>
    <div>count amount: {{ count }}</div>
    <span>
        <button @click="decrementCounter()">-</button>
        <button @click="incrementCounter()">+</button>
    </span>
</template>

<style scoped>

</style>