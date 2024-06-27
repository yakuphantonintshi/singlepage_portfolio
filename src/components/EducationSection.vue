<template>
  <div class="container">
    <div class="row">
        <h1>Education</h1>
    </div>
   <div class="row">
    <div v-if="education?.length">
        <p class="lead" v-for="(education, index) in education" :key="index">
                {{ education }}
            </p>
    </div>
    <Spinner v-else/>
   </div>
  </div>
</template>











<script setup>
 
import { computed, onMounted, ref } from 'vue'
import {useStore} from 'vuex'
import Spinner from '@/components/Spinner.vue'
const store = useStore()
const education = computed(() => store.state.education)
const title = ref()
const cnt = ref(-1)

function repeat(){
    try{
        if (cnt.value == education.value?.length) cnt.value = 0
        title.value = education.value?.at(cnt.value)?.title;
        // setTimeout(repeat, 2000)
        cnt.value ++
    }catch (e) {
        // 
    }
}
onMounted(() => {
    store.dispatch('fetchEducation')
    repeat()
})



</script>

<style>

</style>