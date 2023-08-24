<template>
	<Banner />
  <div class="mt-12 mb-7 mx-8 min-h-[250px]">
    <h1 class="text-center text-4xl text-gray-800">Monte o seu burger!</h1>
    <BurgerForm />
  </div>
</template>

<script>
	import Banner from '../components/Banner'
	import BurgerForm from '../components/BurgerForm'

	export default {
		name: 'HomeView',
		components: {
      Banner,
      BurgerForm
    }
	}
</script>
