<template>
  <main>
    <section class="container top-section">
      <h1 class="heading-primary">Todo List</h1>
      <section class="section-add-list">
        <input v-model="inputTask" class="add-list" type="text" id="fname" name="fname" />
        <button @click="addTask()" type="submit">Add Task</button>
      </section>
    </section>
    <section class="container bottom-section">
      <div v-for="task in listTaskArray" :key="task">
        <div class="task-detail">
          <div>
            <button style="margin-right: 10px;">done</button>
            <span>
              {{ task }}
            </span>
          </div>
          <button>delete</button>
        </div>
      </div>
    </section>
  </main>
</template>

<script setup>
import { ref } from 'vue'

const listTaskArray = ref([])
const inputTask = ref('')

function addTask() {
  console.log(inputTask.value)
  listTaskArray.value.push(inputTask.value)
  inputTask.value = ''
  // console.log(inputTask.value);
}
</script>
