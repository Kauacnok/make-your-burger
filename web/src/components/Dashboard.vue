<template>
	<div class="max-w-[1200px] max-h-[1400px] mx-auto">
		<div>
			<div class="flex flex-wrap font-bold p-3 border-b-[3px] border-gray-800">
				<div class="w-[5%]">#:</div>
				<div class="w-[16%]">Cliente:</div>
				<div class="w-[16%]">Pão:</div>
				<div class="w-[16%]">Carne:</div>
				<div class="w-[16%]">Opcionais:</div>
				<div class="w-[16%]">Ações:</div>
			</div>
		</div>
		<div class="flex flex-wrap">
			<div class="flex flex-wrap p-3 w-full p-3 border-b border-gray-700">
				<div class="w-[5%]">1</div>
				<div class="w-[16%]">João</div>
				<div class="w-[16%]">Pão de trigo</div>
				<div class="w-[16%]">Picanha</div>
				<div class="w-[16%]">
					<ul>
						<li>Salame</li>
						<li>Tomate</li>
					</ul>
				</div>
				<div class="flex">
					<select name="status" class="h-full bg-transparent border-[2px] border-gray-800 text-gray-800 mb-2 p-2 mr-3">
						<option value="">Selecione</option>
					</select>
					<button 
						class="bg-gray-800 text-yellow-500 font-bold border-[2px] rounded border-gray-800 p-2 text-xl mx-auto cursor-pointer transition-[0.5] hover:bg-transparent hover:text-gray-800" 
						type="button"
					>
							Cancelar
					</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	name: "Dashboard"
</script>