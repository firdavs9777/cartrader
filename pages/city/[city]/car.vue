<script setup>
// Router name
const route = useRoute();
const {toTitleCase} = useUtilities()
useHead({
  title: `${
    route.params.make ? toTitleCase(route.params.make) : 'Cars'
  } in ${toTitleCase(route.params.city)}`
});
// using custom layout in car page
definePageMeta({
  layout: 'custom'
});

</script>
<template>
  <div>
    <!-- CARS PAGE -->
    <div class="mt-32 flex">

      <NuxtErrorBoundary>
      <!-- CAR SIDE BAR -->
      <CarSideBar :title="route.params.city" />
      <!-- CAR CARDS -->
      <NuxtPage />
      <template #error="{ error }">
        <div class="text-center mx-auto flex flex-col">
          <h1 class="text-5xk text-red-700 mb-4">Sorry something went wrong</h1>
          <p>An error occurred: {{ error }}</p>
          <button 
          class="text-white bg-red-500 px-10 py-3 rounded"
          @click="error.value = null">Go back</button>
        </div>
      </template>
    </NuxtErrorBoundary>
    </div>
  </div>
</template>
