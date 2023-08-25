<template>
	<div>
		<Message :msg="message" v-show="message" />
		<div class="max-w-[400px] mx-auto ">
			<form @submit="createBurger">
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
						<option v-for="bread in breads" :key="bread.id" :value="bread.type">{{bread.type}}</option>
					</select>
				</div>
				<div class="flex flex-col mb-5">
					<label 
						for="meal"
						class="font-bold mb-3 text-gray-800 py-1 px-3 border-l-[4px] border-yellow-400"
					>
						Escolha a carne do seu Burger:
					</label>
					<select name="meat" id="meat" v-model="meat" class="py-1 px-3 w-[300px]" >
						<option value="">Selecione a sua carne</option>
						<option v-for="meat in meats" :key="meat.id" :value="meat.type">{{meat.type}}</option>
					</select>
				</div>
				<div class="flex flex-col mb-5">
					<label 
						for="optionals"
						class="w-[100%] font-bold mb-3 text-gray-800 py-1 px-3 border-l-[4px] border-yellow-400"
					>
						Selecione os opcionais:
					</label>
					<div class="flex flex-row flex-wrap">
						<div 
							class="flex flex-row flex-wrap gap-2 justify-start w-1/2 mb-5"
							v-for="optional in optionalsData"
							:key="optional.id"
						>
							<input type="checkbox" name="optionals" v-model="optionals" :value="optional.type">
							<span class="font-bold">{{optional.type}}</span>
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
	import Message from './Message'

	export default {
		name: 'BurgerForm',
		data() {
			return {
				breads: null,
				meats: null,
				optionalsData: null,
				name: null,
				bread: null,
				meat: null,
				optionals: [],
				message: null
			}
		},
		components: {
			Message
		},
		methods: {
			async getIngredients() {
				const req = await fetch("http://localhost:3000/ingredients")
				const data = await req.json()

				this.breads = data.breads
				this.meats = data.meats
				this.optionalsData = data.optionals
			},
			async createBurger(event) {
				event.preventDefault()

				const data = {
					name: this.name,
					bread: this.bread,
					meat: this.meat,
					optionals: Array.from(this.optionals),
					status: "Solicitado"
				}

				const dataJson = JSON.stringify(data)

				const req = await fetch('http://localhost:3000/burgers', {
					method: "POST",
					headers: {"Content-Type": "application/json"},
					body: dataJson
				})

				const res = await req.json()

				this.message = `Pedido Nº ${res.id} realizado com sucesso`

				setTimeout(() => {
					this.message = null
				}, 5000)

				this.name = ""
				this.bread = ""
				this.meat = ""
				this.optionals = []
			}
		},
		mounted() {
			this.getIngredients()
		}
	}
</script>