<script setup>
import emitter from 'tiny-emitter/instance'

const items = ref([
        { title: 'Hide Story' },
        { title: 'Hide all from Shahin Alam' },
        { title: 'Report' },
        { title: 'Appriciate the author'},
      ]) 
function showauthor() {
    emitter.emit("show-author")
}      
function showaboutstory() {
    emitter.emit("show-story")
}      
function showreact() {
    emitter.emit("show-react")
}      
function showreviews() {
    emitter.emit("show-review")
}      
</script>
<template>
   <v-card>
        <div class="header_top">
            <div class="">
                <div @mouseenter="showauthor" class="header">
                    <div class="avater">
                        <img src="https://cdn-icons-png.flaticon.com/512/149/149071.png" alt="">
                    </div>
                    <div class="name">
                        <h6>Author</h6>
                        <h5>Shahin Alam</h5>   
                    </div>
                </div>
            </div>
            <div>
                <v-btn icon="mdi-dots-vertical"  elevation="0" id="menu-activator"></v-btn>
                <v-menu activator="#menu-activator">
                <v-list>
                    <v-list-item
                    v-for="(item, index) in items"
                    :key="index"
                    :value="index"
                    >
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                    </v-list-item>
                </v-list>
                </v-menu>
            </div>
        </div>
        <v-divider></v-divider>
        <div @mouseenter="showaboutstory" class="story">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Id, tempore aliquid. Assumenda incidunt minima sapiente deleniti corporis officiis voluptates doloremque omnis et illum hic magnam praesentium numquam culpa rerum ab eius commodi ipsam quaerat esse, itaque dolore atque sed. Veritatis reprehenderit in vitae. Cum in quos inventore repellat officia, sit iure maiores, consequatur, quasi laborum tenetur excepturi maxime corrupti! Voluptatibus voluptatem iste ipsam laudantium, dicta sunt ipsum praesentium, enim sequi provident, quidem recusandae. Animi velit aspernatur consectetur unde delectus aperiam similique, est nemo! Fugiat recusandae optio ut repudiandae, sint corrupti iure ullam commodi modi maiores debitis aperiam, ipsam est et.
        </div>
        <v-divider></v-divider>
        <div class="public_reactions">
           <div class="reaction">
             <div class="btn_container">
                <button @mouseenter="showreact" class="react_btn">
                    React
                </button>
             </div>
             <div class="btn_container">
                <button @mouseenter="showreviews" class="react_btn">
                    Review
                </button>
             </div>
             <div class="btn_container">
                <button class="react_btn">
                    Share
                </button>
             </div>
           </div>
        </div>
    </v-card>
</template>
<style scoped>
.header{
  padding: 10px;
  display: flex;
  justify-content: flex-start;
  gap: 10px;
  align-items: center;
  cursor: pointer;
}
.header_top{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.avater{
    width: 40px;
    height: 40px;
    border-radius: 50%;
    overflow: hidden;
}
.avater img{
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.public_reactions{
    padding: 10px;
}
.reaction{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.reaction .btn_container{
   width: 100%;
}
.react_btn{
    padding: 8px 30px;
    text-transform: uppercase;
    font-size: 12px;
    font-weight: bold;
    letter-spacing: 2px;
    width: 100%;
    border-radius: 5px;
}
.react_btn:hover{
    background-color: #E8EAEB;
}
</style>