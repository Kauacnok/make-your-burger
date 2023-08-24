<template>
	<nav class="flex justify-between items-center bg-gray-800 border-b-[4px] border-gray-700 py-4 px-8">
		<router-link to="/">
			<img :src="logo" :alt="alt" class="w-10 h-10 ">
		</router-link>
		<div>
	    <router-link to="/" class="text-yellow-400 m-4 hover:text-white transition-[0.5s]">Home</router-link> |
	    <router-link to="/orders" class="text-yellow-400 m-4 hover:text-white transition-[0.5s]">Pedidos</router-link>
    </div>
  </nav>
</template>

<script lang="ts">
	export default {
		name: 'Navbar',
		props: ['logo', 'alt']
	}
</script>