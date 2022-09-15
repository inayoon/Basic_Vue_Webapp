# Basic Vue Web-App

### - Mini Vue Website. 
 
## All Studios for Rent in Seoul

### `Home` Page

 <img src="https://user-images.githubusercontent.com/100747899/190280142-c4c39cb6-430c-4728-b503-aadbfe4cb830.gif">
 
 - created all the studios with Card components and properly data-binding
 - used v-for and v-if to show up the Card components and a Discount component
 - used custom event to change parent's data in child's module 
 
 ```JavaScript
 // Card.vue
 <template>
   <div>
     <img :src="studio.image" class="room-img">
     <h4 @click="$emit('openModal', studio.id)">{{studio.title}}</h4>
     <p>${{studio.price}} /month</p>
   </div>    
 </template>
```  
 ```JavaScript
 // App.vue
<Card @openModal="isOpen=true; press=$event" :studio="studio[i]" v-for="(a,i) in studio" :key="a" />
```  
  
    
 ### `Sorting Lowest Price` function
 <img src="https://user-images.githubusercontent.com/100747899/190280555-364f4ee1-d2e3-4bb6-a6e3-11dceafd7669.gif">


 ### `Sorting Highest Price` function
 <img src="https://user-images.githubusercontent.com/100747899/190281451-ec84e971-c3ba-439d-8bb7-27ed77ab038a.gif">  
 
 - created 3 buttons(Price:highest, Price:lowest, Back) for sorting
 - sorted objects with highest price, lowest price and sort back to original(raw data)
 
 ```JavaScript

        methods : {
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
```  
  
    
 ### `Get the Input value` 
  <img src="https://user-images.githubusercontent.com/100747899/190283084-e59605f5-d6f1-4e06-afce-2c73074d3bb3.gif">  
  <img width="355" alt="image" src="https://user-images.githubusercontent.com/100747899/190283390-009a163d-e84f-41a0-a206-45ff21fc17f2.png"><img width="317" alt="image" src="https://user-images.githubusercontent.com/100747899/190283491-b7efa5fb-f27f-4eed-bc01-8e2cacdb5420.png"><img width="332" alt="image" src="https://user-images.githubusercontent.com/100747899/190283600-7e76b8ea-bd7e-4e96-972c-1426d63f637f.png">  
  
 - got the input value to show different amount of rent fee per months that user put
  ```Vue
 <input v-model="month"> 
      <p> {{month}}months selected : ${{studio[press].price * month}}</p>
```
     
     
<img width="354" alt="image" src="https://user-images.githubusercontent.com/100747899/190284111-3eca3c7f-a355-4d51-9dd0-03c184709dc9.png">  <img width="341" alt="image" src="https://user-images.githubusercontent.com/100747899/190284241-bbcb301e-400c-42df-80e5-99c42e98242e.png">
- prevent user from putting not a number or more than 12 by using watcher
 ```JavaScript

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
```  
- used Transition built-in tag for animating the insertion, removal
 ```JavaScript
<transition name="fade">
  <Modal @close ="isOpen=false"   
    :studio="studio" :press="press" 
    :isOpen="isOpen" />
</transition>
```  
  
