<script setup>
import swiper from '~/components/swiper.vue';
import emitter from 'tiny-emitter/instance'
const hasStory = ref(true)
const hasSlideItem = ref(true)

onMounted(() => {
    emitter.on("show-author", () => {
        console.log("emitter event for author")
    })
})
  
</script>
<template>
    <div>
        <div v-if="hasSlideItem" class="ma-2">
            <swiper />
        </div>
        <div v-else class="ma-2">
          <SkeletonList />
        </div>
        <div v-if="hasStory" class="ma-2">
            <div class="card_container">
                <StoryCard />
            </div>
            <div class="card_container">
                <StoryCard />
            </div>
            <div class="card_container">
                <StoryCard />
            </div>
            <div class="card_container">
                <StoryCard />
            </div>
            <div class="card_container">
                <StoryCard />
            </div>
        </div>
        <div v-else class="ma-2">
           <SkeletonCard />
        </div>
    </div>
</template>
<style scoped>
/* story card  */
.card_container{
    margin-bottom: 10px;
}

</style>