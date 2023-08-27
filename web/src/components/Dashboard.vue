<template>
	<div class="max-w-[1200px] max-h-[1400px] mx-auto">
		<Message :msg="message" v-show="message" />
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
			<div class="flex flex-wrap p-3 w-full p-3 border-b border-gray-700" v-for="burger in burgers" :key="burger.id">
				<div class="w-[5%]">{{ burger.id }}</div>
				<div class="w-[16%]">{{ burger.name }}</div>
				<div class="w-[16%]">{{ burger.bread }}</div>
				<div class="w-[16%]">{{ burger.meat }}</div>
				<div class="w-[16%]">
					<ul>
						<li v-for="(optional, index) in burger.optionals" :key="index">
							{{ optional }}
						</li>
					</ul>
				</div>
				<div class="flex justify-center items-center">
					<select name="status" class="bg-transparent border-[2px] border-gray-800 text-gray-800 py-3 p-2 mr-3" @change="updateStatusBurger($event, burger.id)">
						<option value="">Selecione</option>
						<option v-for="s in status" :key="s.id" :value="s.type" :selected="burger.status == s.type">{{ s.type }}</option>
					</select>
					<button 
						class="bg-gray-800 text-yellow-500 font-bold border-[2px] rounded border-gray-800 p-2 text-xl mx-auto cursor-pointer transition-[0.5] hover:bg-transparent hover:text-gray-800" 
						type="button"
						@click="deleteBurger(burger.id)"
					>
							Cancelar
					</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import Message from './Message'

	export default {
		name: "Dashboard",
		data() {
			return {
				burgers: null,
				burgers_id: null,
				status: [],
				message: null
			}
		},
		components: {
			Message
		},
		methods: {
			async getOrders() {
				const req = await fetch('http://localhost:3000/burgers')

				const data = await req.json()

				this.burgers = data

				this.getStatus()
			},
			async getStatus() {
				const req = await fetch('http://localhost:3000/status')

				const data = await req.json()

				this.status = data
			},
			async deleteBurger(id) {
				const req = await fetch(`http://localhost:3000/burgers/${id}`, {
					method: "DELETE"
				})

				const res = await req.json()

				this.message = `Pedido Nº ${id} removido com sucesso!`

				setTimeout(() => {
					this.message = null
				}, 5000)

				this.getOrders()
			},
			async updateStatusBurger(event, id) {
				const option = event.target.value

				const dataJson = JSON.stringify({ status: option })

				const req = await fetch(`http://localhost:3000/burgers/${id}`, {
					method: "PATCH",
					headers: {"Content-Type": "application/json"},
					body: dataJson
				})

				const res = await req.json()

				this.message = `Pedido Nº ${res.id} teve seu status atualizado para ${res.status}`

				setTimeout(() => {
					this.message = null
				}, 5000)
			}
		},
		mounted() {
			this.getOrders()
		}
	}
</script>