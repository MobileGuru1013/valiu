<template>
  <v-container pt-5>
    <h1 class="top-title text-xs-center text-primary mb-5">
      9 Bancos Disponibles
    </h1>
    <v-carousel
      height
      hide-delimiters
      class="top-slider-slider"
      delimiter-icon="stop">
      <v-carousel-item
        v-for="(item, i) in chunkedItems"
        :key="i">
        <v-layout wrap row>
          <v-flex
            xs6
            :text-xs-right="i % 2 === 1"
            v-for="(row, i) in item"
            :key="i">
            <img :src="row.src" style="max-height: 90px; max-width: 90%;">
          </v-flex>
        </v-layout>
      </v-carousel-item>
    </v-carousel>
  </v-container>
</template>

<script>
import $ from 'jquery'
export default {
  data: () => ({
    chunk: 4,
    __setChunkTimeOut: null,
    items: [
      { src: '/images/home/top-slider/available-banks.png' },
      { src: '/images/home/top-slider/best-rate.png' },
      { src: '/images/home/top-slider/guaranteed.png' },
      { src: '/images/home/top-slider/help-center.png' },
      { src: '/images/home/top-slider/sms-notifications.png' },
      { src: '/images/home/top-slider/speed.png' },
      { src: '/images/home/top-slider/safely.png' }
    ]
  }),
  computed: {
    chunkedItems() {
      const original = this.items.slice()
      let items = this.items.slice()
      items = [].concat.apply([], items.map((el, i) => i % this.chunk ? [] : [items.slice(i, i + this.chunk)]))
      const last = items.slice().pop()
      if (last.length !== this.chunk) {
        items[items.length - 1] = original.slice(0, this.chunk - last.length).concat(last)
      }
      return items
    }
  },
  methods: {
    setChunkBasedOnWindowWidth() {
      clearTimeout(this.__setChunkTimeOut)
      this.__setChunkTimeOut = setTimeout(() => {
        const width = $(window).outerWidth()
        this.chunk = width >= 992 ? 4 : (width >= 768 ? 4 : (width >= 576 ? 2 : 2))
      }, 50)
    }
  },
  mounted() {
    this.setChunkBasedOnWindowWidth()
    $(window).resize(() => {
      this.setChunkBasedOnWindowWidth()
    })
  }
}
</script>

<style lang="scss">
.v-window {
  &.v-carousel {
    &.top-slider-slider {
      .v-carousel__next,
      .v-carousel__prev {
        top: 30px;
        width: 200px;
        height: 160%;
      }
    }
  }
}
</style>
