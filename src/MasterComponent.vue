<template>
  <main>
    <section class="container top-section">
      <form @submit.prevent="submit">
        <h1 class="heading-primary text-center">Todo List</h1>
        <section class="section-add-list">
          <!-- <input v-model="inputTask" class="add-list" type="text" id="fname" name="fname" /> -->
          <v-text-field style="width: 23.2rem;" v-model="inputTask" label="Please write down task here"></v-text-field>
          <!-- <button type="submit" @click="addTask()">Add Task</button> -->
          <v-btn color="blue-darken-2" variant="elevated" type="submit" @click="addTask()">
            Add Task
          </v-btn>
        </section>
      </form>
    </section>
    <section class="container bottom-section">
      <div class="task-detail" v-for="(task, index) in listTaskArray" :key="task" :id="index">
        <!-- <div class="task-detail"> -->
        <div class="left-pan">
          <input class="checkbox-icon" @click="finishTask(index)" type="checkbox" style="margin-right: 10px;" />
          <!-- <v-checkbox color="red" label="Checkbox"></v-checkbox> -->
          <span v-bind:class="{ done: isDone }">
            {{ task }}
          </span>
          <!-- </div> -->
        </div>
        <button @click="deleteTask(index)">delete</button>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const listTaskArray = ref([])
const inputTask = ref('')
// const isDone = ref(false)

function addTask() {
  console.log(inputTask.value)
  listTaskArray.value.push(inputTask.value)
  inputTask.value = ''
  // console.log(inputTask.value);
}

function deleteTask(e) {
  console.log(e);
  listTaskArray.value.splice(e, 1);
}

function finishTask(e) {
  alert(e);
  // isDone.value = true;
}
</script>
