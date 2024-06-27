<template>
  <div class="container">
    <div class="row vh-100 align-items-center">
        <div class="col">
            <img src="https://yakuphantonintshi.github.io/myimages/Images/Yakupha.jpg" alt="home-pic" class="img-fluid -75 shadow rounded-top" loading="lazy">

        </div>
        <div class="col">
            <div id="details">
                <h1 class="display-1">Yakupha Ntonintshi</h1>
                <p v-if="title"> I am <span class="span">{{ title }}</span>
                </p>
                <Spinner v-else/>
            </div>

        </div>
    </div>

  </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue'
import {useStore} from 'vuex'
import Spinner from '@/components/Spinner.vue'
const store = useStore()
const jobTitle = computed(() => store.state.jobTitle)
const title = ref('web developer')
const cnt = ref(-1)

function repeat(){
    try{
        if (cnt.value == jobTitle.value?.length) cnt.value = 0
        title.value = jobTitle.value?.at(cnt.value)?.title;
        setTimeout(repeat, 2000)
        cnt.value ++
    }catch (e) {
        // 
    }
}
onMounted(() => {
    store.dispatch('fetchJobTitle')
    repeat()
})

</script>

<style scoped>
span {
    color: rgba(171, 122, 88, 0.71);
    font-family:fantasy;
    size: 50rem;
    text-shadow: 3px 3px 5px rgba(194, 80, 19, 0.5);
}
.span{
    font-size: 3rem;
}
img{
    border-radius: 8px solid brown;
}
/* .container{
    background-image: linear-gradient(to right ,rgb(167, 89, 47), beige);
} */

</style>