<template>
  <v-container class="d-flex">
    <p>{{ indexContent.text }}</p>
    <v-img :src="indexContent.image"></v-img>
  </v-container>
</template>

<script>
export default {
  name: 'IndexPage',
  data: () => ({
    indexContent: []
  }),
  async mounted() {
		this.indexContent = await this.$axios.$get('https://demo-api.vsdev.space/api/elonus/home_page')
	}
}
</script>
