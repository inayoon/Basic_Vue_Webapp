<template>

<transition name="fade">
  <Modal @close ="isOpen=false"   
    :studio="studio" :press="press" 
    :isOpen="isOpen" />
</transition>

<div class="menu">
  <a v-for= "a in menus" :key="a"> {{a}}</a>
</div>

<Discount v-if="showDiscount == true" />

<button @click="priceSort">Price:Lowest</button>
<button @click="priceDesSort">Price:Highest</button>
<button @click="sortBack">Back</button>

<Card @openModal="isOpen=true; press=$event" :studio="studio[i]" v-for="(a,i) in studio" :key="a" />

</template>

<script>
import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data(){
    return {
      showDiscount: true,
      press : 0,
      studio : [...data],
      roomCopy: [...data],
      isOpen : false,
      신고수 : [0,0,0],
      menus: ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },
  methods : {
    increase(){
      this.신고수+= 1;
    },
    priceSort(){
      this.studio.sort(function(a,b){
        return a.price - b.price;
      })
    },
        priceDesSort(){
      this.studio.sort(function(a,b){
        return b.price- a.price;
      })
    },
        sortBack(){
      this.studio = [...this.roomCopy];
    },
  },

  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
} 
</script>

<style>
.fade-leave-from{
  opacity:1;
}
.fade-leave-active{
  transition: all 1s;
}
.fade-leave-to{
  opacity:0;
}

.fade-enter-from{
  transform:translateY(-1000px);
}
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  transform:translateY(0px);
}
.start{
  opacity:0;
  transition :all 1s;
}

.end{
  opacity:1;
}

.discount{
  background:lightgrey;
  padding:10px;
  margin:10px;
  border-radius:5px;
}
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
button{
  font-size: 18px;
  padding: 10px;
  margin: 4px;
  border: 1px solid #eee;
  border-radius: 6px;
}
.black-bg {
  width: 100%; height:100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
} 
.room-img{
  width: 80%;
  margin-top: 30px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color:white;
  padding:10px;
}
</style>
