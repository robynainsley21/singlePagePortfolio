<template>
  <div>
    <NavComp />
    <main class="container-fluid">
      <HomeViewVue />
      <router-view />
    </main>
  </div>

</template>

<script>
import HomeViewVue from './views/HomeView.vue'
import NavComp from '@/components/Navbar.vue'


export default {
  components: {
    HomeViewVue,
    NavComp
  }
}
</script>

<style></style>
