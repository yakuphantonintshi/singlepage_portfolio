<template>
  <div class="container">
    <div class="row">
        <h1>About Me</h1>
    </div>
    <div class="row">
        <div v-if="about?.length"> 
            <p class="lead" v-for="(about, index) in about" :key="index">
                {{ about }}
            </p>
            </div>
        <Spinner v-else/>
    </div>
  </div>
</template>

<script setup>
import { computed, onMounted} from 'vue'
import {useStore} from 'vuex'
import Spinner from '@/components/Spinner.vue'
const store = useStore()
const about = computed(() => store.state.about)

onMounted(() => {
    store.dispatch('fetchAbout')
})
</script>

<style scoped>

</style>