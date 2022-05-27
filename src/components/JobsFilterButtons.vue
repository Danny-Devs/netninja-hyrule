<script setup lang="ts">
import { useJobStore } from '@/stores/jobStore'
import type Job from '@/types/Job'
import { ref, computed } from 'vue'
import type { Ref } from 'vue'

const store = useJobStore()

const changeOrder = (orderBy: keyof Job) => {
  store.jobsList = store.jobsList.sort(compareKeys(orderBy))
}

function compareKeys(key: keyof Job, order: 'asc' | 'desc' = 'asc') {
  return function innerSort(a: Job, b: Job) {
    let comparison = 0
    a[key] > b[key] ? comparison = 1 : comparison = -1
    return order === 'desc' ? comparison * -1 : comparison
  }
}

const addJob = () => {
  store.jobsList.unshift({
    title: 'Coder',
    location: 'zetaville',
    salary: 1000,
    id: (store.jobsList.length + 1).toString(),
  })
}
</script>

<template>
  <div class="filter-buttons">
    <h2>Order by:</h2>
    <button @click="changeOrder('salary')" class="btn">Salary</button>
    <button @click="changeOrder('location')" class="btn">Location</button>
    <button @click="changeOrder('title')" class="btn">Title</button>
    <button @click="addJob" class="btn">Add job</button>
  </div>
</template>

<style scoped>
.filter-buttons h2 {
  margin-bottom: 0.3em;
}
.btn {
  padding: 6px 12px;
  font-size: inherit;
  font-family: inherit;
  margin: 0 0.5em 0.3em 0;
  background-color: #17bf66;
  color: white;
  border-radius: 6px;
  border: none;
  transition: background-color 0.1s, color 0.1s;
}

.btn:hover {
  background-color: white;
  color: #17bf66;
  box-shadow: inset 0 0 0 1px #17bf66;
  box-shadow: 4px 4px 6px #d0d0d0;
  transition: transform 0.08s, box-shadow 0.08s;
}

.btn:active {
  background-color: #17bf66;
  color: white;
  transform: translateY(3px);
  box-shadow: 1px 1px 1px #b8b8b8;
}
</style>
