<script setup>
import heartFilled from '@/assets/heartFilled.png'
import heartOutline from '@/assets/heartOutline.png'
// Using props in Nuxt
const props = defineProps({
  car: Object,
  favored: Boolean
})
// const favored = useState(`favored-${props.car.id}`, () => {
//   return false
// })
// Emitting function from parent 
const emit = defineEmits(['favor'])
</script>
<template>
	<div
        class="relative shadow border w-full overflow-hidden mb-5 cursor-pointer h-[200px]"
        >
        <div class="flex h-full" >
         <!-- Change like and dislike button dynamically using click button -->
          <img  class="absolute w-7 right-5 top-2 z-20" :src="favored? heartFilled: heartOutline" alt="favorite" @click="emit('favor',car.id)"/>
          <img
            :src="car.url"
            alt=""
            class="w-[300px] h-full"
            @click="navigateTo(`/car/${car.name}-${car.id}`)"
          />
          <div class="p-4 flex flex-col">
            <div>
              <h1 class="text-2xl text-blue-700">{{ car.name}}</h1>
              <p class="text-gray-700">
                {{ car.description }}
              </p>
            </div>
            <h1 class="mt-auto text-xl">{{car.price}}</h1>
          </div>
        </div>
		   <!-- <div class="flex h-full">
          <img
            src="https://carwow-uk-wp-3.imgix.net/Volvo-XC40-white-scaled.jpg"
            alt=""
            class="w-[300px] h-full"
          />
          <div class="p-4 flex flex-col">
            <div>
              <h1 class="text-2xl text-blue-700">Volvo XC40</h1>
              <p class="text-gray-700">
                Lorem ipsum dolor sit amet consectetur adipisicing elit.
              </p>
            </div>
            <h1 class="mt-auto text-xl">$39,555</h1>
          </div>
        </div> -->
      </div>
</template>