<template>
  <v-container py-5>
    <v-carousel
      height
      :cycle="false"
      hide-delimiters
      delimiter-icon="stop">
      <v-carousel-item
        v-for="(items, i) in chunkedItems"
        :key="i">
        <v-layout>
          <v-flex
            v-for="(item, i) in items"
            :key="i">
            <img :src="item.src" width="80%">
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
      { src: '/images/home/top-slider/speed.png' },
      { src: '/images/home/top-slider/best-rate.png' },
      { src: '/images/home/top-slider/help-center.png' },
      { src: '/images/home/top-slider/guaranteed.png' },
      { src: '/images/home/top-slider/safely.png' },
      { src: '/images/home/top-slider/sms-notifications.png' }
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
        this.chunk = width >= 992 ? 4 : (width >= 768 ? 3 : (width >= 576 ? 2 : 2))
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
    box-shadow: none;
    .v-window-item {
      min-height: 80px;
    }
    .v-carousel__next,
    .v-carousel__prev {
      top: 30px;
      height: 130%;
      width: 300px;
      cursor: pointer;
      @media (max-width: 768px) {
        width: 100px;
      }
      button {
        width: 100%;
        height: 100%;
        &::before,
        .v-btn__content {
          display: none;
        }
      }
    }
    .v-carousel__prev {
      left: 0;
      background-image: linear-gradient(to right, #ffffff 0%, rgba(255, 255, 255, 0) 100%);
    }
    .v-carousel__next {
      right: 0;
      background-image: linear-gradient(270deg, #ffffff 0%, rgba(255, 255, 255, 0) 100%);
    }
  }
}
</style>
