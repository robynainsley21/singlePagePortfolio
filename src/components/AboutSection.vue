<template>
    <div class="row" id="about-content">
        <div class="col-md-6">
            <img src="" alt="about-img">
        </div>
        <div class="col-md-6">
            <p v-if="about && about.length && about[0]?.text">
                <span>{{ about[0]?.text }}</span>
            </p>
            <div v-else class="d-flex justify-content-center">
                <div class="spinner-border" role="status"></div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
const store = useStore()
const about = computed(() => store.state.about)

onMounted(() => {
    store.dispatch('fetchAbout')
})
</script>

<style></style>