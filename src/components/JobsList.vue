<script setup lang="ts">
import { useJobStore } from '@/stores/jobStore'
import JobsFilterButtons from './JobsFilterButtons.vue'

const store = useJobStore()

</script>

<template>
  <div class="job-list">
    <JobsFilterButtons />
    <ul>
      <li v-for="job in store.jobsList" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <p>{{ job.salary }} rupees</p>
        </div>
        <div class="description">
          <p>
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Sapiente
            saepe nemo laboriosam enim eligendi ab nihil quidem et explicabo
            quasi dicta nesciunt dolorum, quis repellat sunt deserunt itaque
            quisquam sit?
          </p>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.job-list ul {
  padding: 0;
}
.job-list li {
  list-style-type: none;
  background: white;
  padding: 16px;
  margin: 16px 0;
  border-radius: 4px;
  box-shadow: 6px 6px 6px rgb(218, 218, 218);
  border: 1px solid var(--vt-c-divider-dark-1);
}
.job-list h2 {
  margin: 0 0 10px;
  text-transform: capitalize;
}
.salary {
  display: flex;
}
.salary img {
  width: 30px;
}
.salary p {
  color: #17bf66;
  font-weight: bold;
  margin: 10px 4px;
}
</style>
