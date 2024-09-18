<template>
  <div class="row" id="landing-content">
      <h1 class="landing-title">Hi, I'm <span>Robyn</span>.</h1>
    <div class="
       image-box border-animation">
      <img class="landing-img" src="https://robynainsley21.github.io/images/images/headshot.JPG" alt="landing-img"
        loading="lazy">
      <div class="landing-text">
        <h4>Robyn Carnow</h4>
        <p v-if="jobTitle?.length">
          <span>{{ jobTitle[0]?.title }}</span>
        </p>
        <SpinnerComp v-else />
      </div>
    </div>
  </div>
</template>

<script setup>
import SpinnerComp from '@/components/Spinner.vue'
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
const store = useStore()
const jobTitle = computed(() => store.state.jobTitle)
onMounted(() => {
  store.dispatch('fetchJobTitle')
})
</script>

<style></style>