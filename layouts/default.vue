<template>
  <v-app dark>
    <Header />
    <v-row>
      <v-col class="col-4 col-md-2">
        <nav class="d-flex flex-column">
          <v-btn outlined class="mb-5">
            <nuxt-link to="/" class="white--text">Главная</nuxt-link>
          </v-btn>
          <v-btn outlined class="mb-5">
            <nuxt-link to="/about" class="white--text">О нас</nuxt-link>
          </v-btn>
          <v-btn outlined>
            <nuxt-link to="/news" class="white--text">Главная</nuxt-link>
          </v-btn>
        </nav>
        <div class="mt-10">
          <p class="text-center">Зарегистрировано погодных событий: 
            <span class="font-weight-bold text-decoration-underline">{{ eventsCount.events }}</span>
          </p>
          <v-img :src="require('~/static/left_widget_img.jpg')" width="190px" class="ml-auto mr-auto"></v-img>
        </div>
      </v-col>
      <v-col class="col-10 col-sm-6 col-md-8">
        <nuxt />
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
import Header from "@/components/Header"

export default {
  name: 'DefaultLayout',
  components: { Header },
  data: () => ({
    eventsCount: []
  }),
  async mounted() {
		this.eventsCount = await this.$axios.$get('https://demo-api.vsdev.space/api/elonus/left_widget')
	}
}
</script>

<style>

a {
  text-decoration: none;
}

</style>
