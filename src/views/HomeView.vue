<script setup lang="ts">
import {ref} from 'vue'


interface Restaurant {
  name?:string,
  address?:string,
  status?:RestaurantStatus,
  dishes?: Dish[]
}

// type RestaurantStatus  = 'Want To Try' | 'Recommended'| 'Do Not Recommended' | 'Must Try'


 const restaurantList = ref<Restaurant[]>([])
 const newRestaurant = ref<Restaurant>({})
 
 const ALL_STATUS = ['Want to Try','Recommend','Must Try']

 type RestaurantStatus = typeof ALL_STATUS

 const statusList = [
   'Want To Try',
    'Recommended',
    'Do Not Recommended',
    'Must Try'

 ]

 function addRestaurant() {
   restaurantList.value.push({
    name: newRestaurant.value.name,
    address: '',
    status: 'Want To Try',
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
      <!-- <div>
      <label for="restaurant-address">Restaurant Address</label>
      <input id="restaurant-address" v-model="newRestaurant.address" type="text"/>
      <button type="submit">Add restaurant</button> 
      </div> -->
      <div>
      <label for="restaurant-status">Restaurant Status</label>
       <select name ="restaurant-status"
        id="restaurant-status">
      <option v-for="status in statusList" :value="status" :key="status">{{ status }}</option> 
      </select>
      </div>
    </form>
    <ul>
       <li v-for="restaurant in restaurantList" :key ="restaurant">
         {{ restaurant.name }}
      </li>
    </ul>
  </main>
</template>
