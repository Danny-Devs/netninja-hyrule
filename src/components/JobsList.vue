<script setup lang="ts">
import { useJobStore } from '@/stores/jobStore'
import JobsFilterButtons from './JobsFilterButtons.vue'

const store = useJobStore()
</script>

<template>
  <div class="job-list">
    <div class="title-bar">
      <img class="heart-image" src="../assets/heart.svg" alt="site logo" />
      <h1>Hyrule Jobs</h1>
    </div>
    <JobsFilterButtons />
    <transition-group name="list" tag="ul">
      <li v-for="job in store.jobsList" :key="job.id">
        <h2>{{ job.title }} in {{ job.location }}</h2>
        <div class="salary">
          <img class="rupee-image" src="../assets/rupee.svg" alt="rupee coin" />
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
    </transition-group>
  </div>
</template>

<style scoped>
.job-list {
  max-width: 960px;
  margin: 40px auto;
}
.title-bar {
  display: flex;
  justify-content: center;
}
.heart-image {
  width: 60px;
  margin-right: 20px;
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
.job-list h1 {
  text-align: center;
  margin-bottom: 0.5em;
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
.list-move {
  transition: all 0.7s;
}
</style>
