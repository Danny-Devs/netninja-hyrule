<script setup lang="ts">
import JobsList from '../components/JobsList.vue'

// Reference: How to type props
// const props = defineProps<{
//   foo: {type: String, required: true},
//   bar: Number
// }>()

// // must use 'Ref' when typing reactive objects like this
// const age: Ref<number | string> = ref(25)
</script>

<template>
  <JobsList />
</template>

<style scoped>

</style>
