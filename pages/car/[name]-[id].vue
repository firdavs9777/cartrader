<script setup>
const route = useRoute()
const {toTitleCase} = useUtilities()

const { cars } = useCars()

// Shows name of the router
useHead({title: toTitleCase (route.params.name)})

// Using Custom Layout and put content inside custom layout
definePageMeta({
	layout: 'custom'
})

// If  route params id is equal to the id of car's id
// return the value 
const car = computed(() => {
	return cars.find((c) => {
		return c.id === parseInt(route.params.id)
	})
})
// Custom Error 
if(!car.value)
{
	throw createError({
		statusCode: 404,
		message: `Car with id of ${route.params.id} does not exist`
	})
}

</script>
<template>
	<div >
			<CarDetailHero :car="car" />
			<CarDetailAttributes :features="car.features"/>
			<CarDetailDescription :description="car.description" />
			<CarDetailContact  />
	</div>
</template>
