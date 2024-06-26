<template>
  <div class="container">
    <div class="row">
        <div class="col">
            <img src="https://yakuphantonintshi.github.io/myimages/Images/Yakupha.jpg" alt="home-pic" class="img-fluid" loading="lazy">

        </div>
        <div class="col">
            <div id="details">
                <h1 class="display-1">Yakupha Ntonintshi</h1>
                <span>{{ jobTitle [0].title }}</span>
            </div>

        </div>
    </div>

  </div>
</template>

<script setup>
import { computed, onMounted } from 'vue'
const jobTitle = computed(() => this.$store.state.jobTitle)
onMounted(() => {
    this.$store.dispatch('fetchJobTitle')
})
</script>

<style scoped>

</style>