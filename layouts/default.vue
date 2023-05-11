<script setup>
import aboutAuthor from '~/components/story/aboutAuthor.vue'
import aboutReact from '~/components/story/aboutReact.vue'
import aboutReview from '~/components/story/aboutReview.vue'
import aboutStory from '~/components/story/aboutStory.vue'
import emitter from 'tiny-emitter/instance'

const isLoading = ref(true)
const isAuthor = ref(true)
const isStory = ref(false)
const isReact = ref(false)
const isReview = ref(false)
const colorMode = useColorMode()
console.log(colorMode.preference)
onMounted(() => {
    isLoading.value = false
    emitter.on("show-author", () => {
        isAuthor.value = true
        isStory.value = false
        isReact.value = false
        isReview.value = false
    })
    emitter.on("show-story", () => {
        isStory.value = true
        isAuthor.value = false
        isReact.value = false
        isReview.value = false
    })
    emitter.on("show-react", () => {
        isReact.value = true
        isStory.value = false
        isAuthor.value = false
        isReview.value = false
    })
    emitter.on("show-review", () => {
        isReview.value = true
        isReact.value = false
        isStory.value = false
        isAuthor.value = false
    })
})

</script>
<template>
    <div>
        <div v-if="!isLoading">
            <v-layout>
                    <v-app-bar :elevation="1">
                            <v-app-bar-title>Website</v-app-bar-title>
                            <template v-slot:append>
                            <v-btn icon="mdi-dots-vertical"></v-btn>
                            </template>
                    </v-app-bar>
                    <!-- drawer left  -->
                    <v-navigation-drawer
                    :elevation="2"
                    class=""
                    >
                 
                    <div class="pa-2 category">
                      <h5>
                        Categories
                      </h5>
                      
                    </div>
                    <v-divider></v-divider>
            
                    <v-list density="compact" nav>
                    <v-list-item prepend-icon="mdi-star" title="Fairy Tale" value="fairy"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="Hounted Story" value="Hounted"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="Life Story" value="Life"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="Dark Story" value="Dark"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="Kids Story" value="Kids"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="Historical Story" value="Historical"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="true Story" value="true"></v-list-item>
                    <v-list-item prepend-icon="mdi-star" title="Comic Story" value="Comic"></v-list-item>
                    </v-list>
                    </v-navigation-drawer>
                    <!-- drawer left end  -->
                    <!-- drawer right  -->
                    <v-navigation-drawer location="right" :elevation="2" 
                    
                    
                >
                  
            
                  
                    <about-author v-show="isAuthor" class="mb-2" />
                    <about-story  v-show="isStory" class="mb-2"/>
                    <about-react  v-show="isReact" class="mb-2"/>
                    <about-review v-show="isReview" class="mb-2" />
                    </v-navigation-drawer>
                    <!-- drawer right end  -->
                    <v-main>
                        <slot />
                    </v-main>
                </v-layout>
        </div>
        <div v-else class="w_full">
           <div class="loading">
             <h4>Loading...</h4>
           </div>
        </div>
    </div>
</template>
<style>
  body {
  background-color: #E9EBEC;
  color: rgba(0,0,0,0.8);
}
.dark-mode body {
  background-color: #091a28;
  color: #ebf4f1;
}
.sepia-mode body {
  background-color: #f1e7d0;
  color: #433422;
}
  .wrapper{
    max-width: 1000px;
    margin: 0 auto;
    box-sizing: border-box;
  }
  .w_full{
    width: 100%;
  }
  .loading{
    height: 80vh;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .loading h4{
    font-size: 35px;
    font-weight: bold;
    color: lightgray;
  }
  .bg_img{

    background-image: url(https://i.postimg.cc/15vnX2z8/8821181-457.jpg);

    background-position: center;
    background-size: contain;
    background-repeat: no-repeat;
  }
  
  .category{
    padding: 8px 20px !important;
    border-bottom: 1px solid lightgray;
  }
  .category h5{
    font-size: 15px;
    color: gray;
    text-transform: uppercase;
    letter-spacing: 1px;
    padding-top: 5px;
  }
</style>