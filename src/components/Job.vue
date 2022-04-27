<template>
  <div class="flex w-full gap-6 bg-white rounded-lg shadow-lg p-8 relative overflow-hidden">
    <div v-if="job.featured" class="absolute h-full bg-cyan-base w-1 left-0 top-0" />

    <img :src="job.logo">
    <div class="space-y-2 flex-grow">
      <div class="flex items-center gap-2">
        <div class="text-sm font-medium text-cyan-base">{{ job.company }}</div>
        <div v-if="job.new" class="bg-cyan-base rounded-full px-2 text-white uppercase text-tiny">New!</div>
        <div v-if="job.featured" class="bg-gray-900 rounded-full px-2 text-white uppercase text-tiny">Featured</div>
      </div>
      <div class="font-medium">
        {{ job.position }}
      </div>
      <div class="flex items-center space-x-4 text-sm text-gray-400">
        <div>{{ job.postedAt }}</div>
        <FaIcon :icon="['fas', 'circle']" class="w-1"/>
        <div>{{ job.contract }}</div>
        <FaIcon :icon="['fas', 'circle']" class="w-1"/>
        <div>{{ job.location }}</div>
      </div>
    </div>
    <div class="ml-auto flex items-center justify-end gap-2">
      <div v-for="language of job.languages" :key="language" class="rounded px-2 bg-cyan-light text-cyan-base text-tiny font-semibold cursor-pointer">
        {{ language }}
      </div>
    </div>
  </div>
</template>

<script>
import {defineComponent} from "vue";

export default defineComponent({
  name: 'Job',
  props: {
    job: {
      type: Object,
      required: true
    }
  }
})
</script>