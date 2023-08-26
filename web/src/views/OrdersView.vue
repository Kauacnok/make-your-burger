<template>
	<div class="mt-12 mb-7 mx-8 min-h-[450px]">
		<h1 class="text-center text-4xl text-gray-800">Gerenciar pedidos</h1>
		<Dashboard />
	</div>
</template>

<script>
	import Dashboard from '../components/Dashboard'
	export default {
		name: 'OrdersView',
		components: {
			Dashboard
		}
	}
</script>
