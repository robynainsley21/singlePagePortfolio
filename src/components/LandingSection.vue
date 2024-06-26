<template>
  <div class="row" id="landing-content">
    <div class="">
      <h1 class="landing-title">Hi, I'm <span>Robyn</span>.</h1>
    </div>
    <div class="
       image-box border-animation">
      <img class="landing-img" src="https://robynainsley21.github.io/images/images/headshot.JPG" alt="landing-img"
        loading="lazy">
      <div class="landing-text">
        <h4>Robyn Carnow</h4>
        <p v-if="jobTitle?.length">
          <span>{{ jobTitle[0]?.title }}</span>
        </p>
        <div v-else class="d-flex justify-content-center">
          <div class="spinner-border" role="status"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
const store = useStore()
const jobTitle = computed(() => store.state.jobTitle)
onMounted(() => {
  store.dispatch('fetchJobTitle')
})
</script>

<style></style>