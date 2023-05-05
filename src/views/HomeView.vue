<script setup lang="ts">
import {ref} from 'vue'


interface Restaurant {
  name?:string,
  address?:string,
  status?:string,
  dishes?: Dish[]
}


 const restaurantList = ref<Restaurant[]>([])
 const newRestaurant = ref<Restaurant>({})

 function addRestaurant() {
   restaurantList.value.push({
    name: newRestaurant.value.name,
    address: '',
    status: '',
    dishes: []
  })
 }

</script>

<template>
  <main>
    <pre>
      {{ newRestaurant }}
    </pre>
    <form @submit.prevent="addRestaurant">
       <div>
          <label for="restaurant-name">Restaurant Address</label>
      <input id="restaurant-name" v-model="newRestaurant.name" type="text"/>
      <button type="submit">Add restaurant</button> 
       </div>
   <div>
      <label for="restaurant-address">Restaurant Address</label>
      <input id="restaurant-address" v-model="newRestaurant.address" type="text"/>
      <button type="submit">Add restaurant</button> 
      </div>
    </form>
    <ul>
       <li v-for="restaurant in restaurantList" :key ="restaurant">
         {{ restaurant.name }}
      </li>
    </ul>
  </main>
</template>
