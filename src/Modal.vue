<template>
  <div class="black-bg" v-if="isOpen==true">
    <div class="white-bg">
      <Discount></Discount>
      <h4>{{studio[press].title}}</h4>
      <img :src="studio[press].image">
      <p>{{studio[press].content}}</p>
      <input v-model="month"> 
      <p> {{month}}months selected : ${{studio[press].price * month}}</p>
      <button @click="$emit('close')">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  name : 'aModal',
  data(){
    return{
      month:1 ,
    }
  },
  watch:{
    month(a){
    if(isNaN(a)){
      alert("Please enter only a number");
      this.month = 1;
    }
    if(a>12){
      alert("Please enter below 12 months");
      this.month = 1;
    }
  },
},
  props: {
    studio : Array,
    press : Number,
    isOpen: Boolean,
  }
}
</script>

<style>

</style>