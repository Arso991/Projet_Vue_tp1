<template>
    <div class="todo__content__task__item">
        <label for="" :class="element.is_finished ? 'active' : ''">{{ element.name }}</label>
        <starIcon class="star" :is_important="element.is_important" @click="markAsImportant(element)"></starIcon>
        <input type="checkbox" name="task" id="task" v-model="element.is_finished" v-bind:checked="element.is_finished">
        <trash class = 'remove' @click='removeTask'></trash>
    </div>
</template>

<script setup lang="ts">

import starIcon from '@/components/starIcon.vue'
import {task} from '@/types/task'
import trash from '@/components/trash.vue'

const emits = defineEmits(['bonjour'])
const props = defineProps<{
    element:task
}>()

function markAsImportant (element:task){
    element.is_important = !element.is_important
}

function removeTask (){
    emits('bonjour',props.element)
   /*  console.log(props.element); */
}

</script>

<style>
.active {
    color: gray;
    text-decoration: line-through;
}

.star {
    width: .8rem;
    color: black;
    cursor: pointer;
}

.remove{
    color: red;
    font-size: .8rem;
    padding: .2rem;
    border-radius: 5px;
    cursor: pointer;
}
</style>