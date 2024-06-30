<template>
  <div v-if="contact?.length">
    
  </div>
  <SpinnerComp v-else />
</template>

<script>
import SpinnerComp from '@/components/Spinner.vue'
import { computed, onMounted } from 'vue'
import { useStore } from 'vuex'
const store = useStore()
const contact = computed(() => store.state.contact)

onMounted(() => {
    store.dispatch('fetchContact')
})
</script>

<style>

</style>