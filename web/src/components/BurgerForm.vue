<template>
	<div>
		<p>Componente de mensagem</p>
		<div class="max-w-[400px] mx-auto ">
			<form>
				<div class="flex flex-col mb-5">
					<label 
						for="name"
						class="font-bold mb-3 text-gray-800 py-1 px-3 border-l-[4px] border-yellow-400"
					>
						Nome do cliente:
					</label>
					<input 
						type="text" 
						v-model="name" 
						name="name"
						class="py-1 px-3 w-[300px]" 
						placeholder="Digite seu nome" 
					/>
				</div>
				<div class="flex flex-col mb-5">
					<label 
						for="bread"
						class="font-bold mb-3 text-gray-800 py-1 px-3 border-l-[4px] border-yellow-400"
					>
						Escolha o pão:
					</label>
					<select name="bread" id="bread" v-model="bread" class="py-1 px-3 w-[300px]" >
						<option value="">Selecione o seu pão</option>
						<option value="integral">Integral</option>
					</select>
				</div>
				<div class="flex flex-col mb-5">
					<label 
						for="meal"
						class="font-bold mb-3 text-gray-800 py-1 px-3 border-l-[4px] border-yellow-400"
					>
						Escolha a carne do seu Burger:
					</label>
					<select name="meal" id="meal" v-model="meal" class="py-1 px-3 w-[300px]" >
						<option value="">Selecione o seu pão</option>
						<option value="maminha">Maminha</option>
					</select>
				</div>
				<div class="flex flex-col mb-5">
					<label 
						for="meal"
						class="w-[100%] font-bold mb-3 text-gray-800 py-1 px-3 border-l-[4px] border-yellow-400"
					>
						Selecione os opcionais:
					</label>
					<div class="flex flex-row flex-wrap">
						<div class="flex flex-row flex-wrap gap-2 justify-start w-1/2 mb-5">
							<input type="checkbox" name="optionals" v-model="optionals" value="salame">
							<span class="font-bold">Salame</span>
						</div>
						<div class="flex flex-row flex-wrap gap-2 justify-start w-1/2 mb-5">
							<input type="checkbox" name="optionals" v-model="optionals" value="salame">
							<span class="font-bold">Salame</span>
						</div>
						<div class="flex flex-row flex-wrap gap-2 justify-start w-1/2 mb-5">
							<input type="checkbox" name="optionals" v-model="optionals" value="salame">
							<span class="font-bold">Salame</span>
						</div>
					</div>
				</div>
				<div class="flex justify-center items-center">
					<input 
						type="submit" 
						value="Criar meu Burger"
						class="bg-gray-800 text-yellow-400 font-bold border-[2px] border-gray-800 rounded px-8 py-3 text-xl cursor-pointer transition hover:bg-transparent hover:text-gray-800" 
					>
				</div>
			</form>
		</div>
	</div>
</template>

<script>
	export default {
		name: 'BurgerForm'
	}
</script>