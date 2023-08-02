<template>
    <div class="container">
        <div class="todo_content">
            <div class="todo__content__title">
                <h1>TO-DO-LIST</h1>
            </div>
            <form @submit.prevent="addTodo">
                <input v-model="newTodo">
                <btn/>
            </form>

            <div class="todo__content__task">
                <task @bonjour="deleteTask" v-for="element in todoTab" :element="element"></task>
            </div>
        </div>
        <!-- <button @click="count++">
            Le nombre de clique est : {{ count }}
        </button> -->
    </div>
</template>

<script setup lang="ts">
import task from '@/components/task.vue'
import btn from '@/components/btn.vue'
import { ref } from 'vue';
const count = ref()

const newTodo = ref('');


/* interface Tab {
    name : String,
    is_finished : boolean
} */

const todoTab /* : Tab[] */ = ref([
    {
        name: 'Boire',
        is_finished: true,
        is_important:false
    },
    {
        name: 'Voler',
        is_finished: false,
        is_important:true
    },
    {
        name: 'Lessive',
        is_finished: true,
        is_important:false
    },
    {
        name: 'Manger',
        is_finished: false,
        is_important:true
    },
    {
        name: 'Dormir',
        is_finished: true,
        is_important:false
    },

])

function deleteTask (element){
   const index = todoTab.value.findIndex((item)=>{
    return item.name == element.name
   })
   console.log(index);
   if(index > -1){
    todoTab.value.splice(index,1)
   }
   
}

function addTodo() {
    todoTab.value.push({ name: newTodo.value, is_finished: false, is_important:false })
    newTodo.value = ''
}
</script>


<style scoped>
form button {
    padding: .5rem;
    background-color: green;
    border: none;
    border-radius: 5px;
    display: block;
    color: white;
    font-weight: 600;
}

form {
    display: flex;
    gap: 1rem;
    justify-content: center;
}

.container {
    padding: 0 5rem;
    display: flex;
    justify-content: center;
}

input {
    outline: none;
}

.todo_content {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    justify-content: center;
    padding: 1rem;
    border: 1px solid gray;
    font-family: 'system-ui', 'sans-serif';
}

.todo__content__title {
    display: flex;
    justify-content: center;
}

.todo__content__title h1 {
    font-size: 2.5rem;
    color: green;

}

.todo__content__task {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 100%;
    padding: 0 .5rem;
}

.todo__content__task__item {
    display: flex;
    justify-content: space-between;
}

.todo__content__task__item {
    font-size: 1.5rem;
}
</style>