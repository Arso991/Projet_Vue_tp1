<script setup lang="ts">

import { ref } from 'vue';

const newTodo = ref('');

/* interface Tab {
    name : String,
    is_finished : boolean
} */

const todoTab /* : Tab[] */ = ref([
    {
        name: 'Boire',
        is_finished: true
    },
    {
        name: 'Voler',
        is_finished: false
    },
    {
        name: 'Lessive',
        is_finished: true
    },
    {
        name: 'Manger',
        is_finished: false
    },
    {
        name: 'Dormir',
        is_finished: true
    },
    
])
function addTodo (){
    todoTab.value.push({name: newTodo.value, is_finished:false})
    newTodo.value =''
}
</script>

<template>
    <!-- <button @click="count++">
       Le nombre de clique est : {{ count }}
    </button> -->
    <div class="container">
        <div class="todo_content">
            <div class="todo__content__title">
                <h1>TO-DO-LIST</h1>
            </div>
            <form @submit.prevent="addTodo">
                <input v-model="newTodo">
                <button>Ajouter</button>
            </form>
            
            <div class="todo__content__task">
                <div v-for="element in todoTab" class="todo__content__task__item">
                    <div v-if="element.is_finished" class="line">
                        <label for="" :class="element.is_finished ? 'active' : ''">{{ element.name }}</label>
                        <input type="checkbox" name="task" id="task" v-bind:checked="element.is_finished">
                    </div>
                    <div v-else>
                        <label for="" :class="element.is_finished ? 'active' : ''">{{ element.name }}</label>
                        <input type="checkbox" name="task" id="task" v-bind:checked="element.is_finished">
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
button{
    margin-top: 1rem;
}
.container{
    padding: 0 5rem;
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
    font-size: 4rem;
    color: green;

}

.todo__content__task {
    display: flex;
    justify-content: center;
    flex-direction: column;
    width: 100%;
    padding: .5rem;
}

.todo__content__task__item {
    display: flex;
    justify-content: space-between;
}

.todo__content__task__item {
    font-size: 2rem;
}

.active {
    color: green;
}

.line {
    text-decoration: line-through;
}
</style>