<template>
  <div class="h-screen flex flex-col overflow-y-auto bg-cyan-light">
    <Header class="flex-shrink-0" />
    <div class="flex-grow container mx-auto max-w-6xl m-20 space-y-6">
      <Job
          v-for="job of jobs"
          :key="job.id"
          :job="job"
      />
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import {defineComponent} from "vue";
import axios from 'axios'
import Job from './components/Job.vue'

export default defineComponent({
  name: 'App',
  components: { Header, Job },
  data: () => ({
    jobs: []
  }),
  async mounted() {
    const response = await axios.get('/api/jobs')
    this.jobs = response.data
  }
})
</script>