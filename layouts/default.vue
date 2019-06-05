<template>
  <v-app>
    <v-content>
      <HomeHeader />
      <nuxt />
    </v-content>
  </v-app>
</template>

<script>
import HomeHeader from '@/components/pages/home/header'
export default {
  components: {
    HomeHeader
  }
}
</script>
