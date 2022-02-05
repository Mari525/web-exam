<template>
  <v-container>
	<v-btn outlined class="mb-10">Добавить событие</v-btn>
	<v-row>
		<v-col class="d-flex align-stretch justify-md-space-around flex-wrap">
			<v-card elevation="2" outlined shaped width="300" class="mb-10"
			v-for="event in eventsList" :key="event.id" :event="event"
			>
				<v-card-title>Событие {{ event.id }}</v-card-title>
				<v-card-text>
					<v-img :src="cardImg(event.type)" width="290"></v-img>
				</v-card-text>
				<v-card-text> Тип: {{ event.type }} </v-card-text>
				<v-card-text> Дата: {{ event.date }} </v-card-text>
				<v-card-text> Количество жертв: {{ event.victims }} </v-card-text>
				<v-card-text> Сила: {{ event.acid_power }} </v-card-text>
			</v-card>
		</v-col>
	</v-row>		
	</div>
  </v-container>
</template>

<script>
export default {
  	name: 'events',
  	data: () => ({
    	eventsList: []
  	}),
  	async mounted() {
		this.eventsList = await this.$axios.$get('https://demo-api.vsdev.space/api/elonus/events')
	},
	methods: {
		cardImg(type) {
			if (type === "acid_rain") {
				return require("~/static/rain_img.jpg")
			}
			else if (type === "hurricane") {
				return require("~/static/hurricane_img.jpg")
			}
			else if (type === "earthquake") {
				return require("~/static/earthquake_img.jpg")
			}
		}
	}
}
</script>

<style>

</style>