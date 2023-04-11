<script setup>
// Getting title from navigation title
const props = defineProps({
  title: String
})
const modal = ref({
  make: false,
  location: false,
  price: false
})

const city = ref('')
  // Change the modal location from true to false,from false to true
const updateModal = (key) => {
  modal.value[key] = !modal.value[key]
} 
// using router
const route = useRoute();

// Change the location when apply clicked
const onChangeLocation = () => {
  if(!city.value) return;
// if( city value is equal to integer or boolean create Custom Error Popup)
  if(!isNaN(parseInt(city.value)))
  {
    throw createError({
      statusCode: 400,
      message: "Invalid city formal"
    })
  }
  // Close the div and navigate to update the router
  updateModal("location")
  navigateTo(`/city/${city.value}/car/${route.params.make}`)
  city.value = ''
}
</script>
<template>
	 <div class="shadow border w-64 mr-10 z-30 h-[190px]">
   <div class="p-5 flex justify-between relative cursor-pointer border-b">
     <h3>Location</h3>
     <h3 class="text-blue-400 capitalize" @click="updateModal('location')"> {{  route.params.city }}</h3>
     <div class="absolute border shadow left-56 p-5 top-1 -m-1 bg-white" v-if="modal.location">
           <input type="text" class="border p-1 rounded" v-model="city" />
           <button class="bg-blue-400 w-full mt-2 rounded text-white p-1" @click="onChangeLocation" >
             Apply
           </button>
         </div>
   </div>
   <div class="p-5 flex justify-between relative cursor-pointer border-b">
  <h3>Make</h3>
  <h3 class="text-blue-400 capitalize">{{title}}</h3>
</div>
	 </div>

</template>