<template>
  <v-container>
	<v-card elevation="2" outlined shaped width="300"
	v-for="event in eventsList" :key="event.id" :event="event"
	>
		<v-card-text> Тип: {{ event.type }} </v-card-text>
		<v-card-text> Дата: {{ event.date }} </v-card-text>
		<v-card-text> Количество жертв: {{ event.victims }} </v-card-text>
		<v-card-text> Сила: {{ event.acid_power }} </v-card-text>
	</v-card>
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
	}
}
</script>

<style>

</style>