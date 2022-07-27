<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder'  : null, 'task']">
    <!-- Instead of adding class of task you could add scoped to the style tag and use div to style the
    component since it is the only div -->
    <!--The 'task' at the end is the div class-->
    <!--If task reminder is true the reminder class styling is used to add a green border
    to the left of the task to indicate it is active and if it is false the task class is used in 
    styling as it has no border-left color-->
    <h3>
        {{ task.text }}
        <i @click="$emit('delete-task', task.id)" class="fa-solid fa-xmark"></i>
    </h3>
    <p>{{task.day}}</p>
  </div>
</template>

<script>
    export default{
        name: 'Task',
        props:{
            task: Object
        }, 
    }
</script>

<style>
    .fa-solid{
        color:red;
    }
    .task{
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }
    .task.reminder{
        border-left:5px solid green;
    }
    .task h3{
        display:flex;
        align-items:center;
        justify-content: space-between;
    }
</style>