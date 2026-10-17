<script setup>
import { ref, watch, onMounted } from 'vue';

const text = ref('')
const tasks = ref([]);

onMounted(() => {
  const saved = localStorage.getItem("tasks")
  if(saved !== null) {
    tasks.value = JSON.parse(saved)
  }
})

watch(tasks, () => {
  localStorage.setItem("tasks", JSON.stringify(tasks.value))
}, { deep: true })


function addTask() {
    if(text.value === "") {
      return;
    }
    else {
      tasks.value = [...tasks.value, { text: text.value, done: false}]
      text.value = ""
    }
  }

  function removeTask(index) {
   tasks.value = tasks.value.filter((t, i) => i !== index)
  }

  function toggleTask(index) {
    tasks.value = tasks.value.map((t, i) => i === index ? {...t, done: !t.done} : t)
  }

</script>

<template>

  <input v-model="text"></input>
  <button @click="addTask"> Dodaj </button>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span :class="{ done: task.done }"> {{ task.text}} </span>
      <button @click="removeTask(index)"> Usuń </button>
      <button @click="toggleTask(index)"> Zrobione </button>
    </li>
  </ul>



</template>

<style scoped>
.done {
  text-decoration: line-through;
}

</style>
