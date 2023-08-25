<template>
	<div class="bg-gray-100 text-blue-700 border-[2px] border-blue-100 rounded p-3 max-w-[400px] my-8 mx-auto">
		<p>{{ msg }}</p>
	</div>
</template>

<script>
	export default {
		name: 'Message',
		props: {
			msg: String
		}
	}
</script>