<template>
  <div>
    <img :src="studio.image" class="room-img">
    <h4 @click="$emit('openModal', studio.id)">{{studio.title}}</h4>
    <p>${{studio.price}} /month</p>
  </div>    
</template>

<script>
export default {
  name: 'aCard',
  props:{
    studio : Object,
  }
}
</script>

<style>

</style>