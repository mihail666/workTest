<template class="base">
  <taskCreate />
  <taskHeader />
  <taskPage />
</template>

<script>
import taskPage from '@/components/taskPage.vue'
import taskCreate from '@/components/taskCreate.vue'
import taskHeader from '@/components/taskHeader.vue'
export default {
  components: {
    taskPage,
    taskHeader,
    taskCreate
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
</style>
