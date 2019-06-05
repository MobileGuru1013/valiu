<template>
  <v-container py-5>
    <h1 class="top-title text-xs-center text-primary mb-5">
      9 Bancos Disponibles
    </h1>
    <v-carousel
      height
      hide-controls
      hide-delimiters
      class="available-banks"
      delimiter-icon="stop">
      <v-carousel-item
        v-for="(row, rowIndex) in chunkedBanks"
        :key="rowIndex">
        <v-layout align-center justify-center text-xs-center row>
          <v-flex
            v-for="(item, itemIndex) in row"
            :key="itemIndex">
            <img :src="item.src" style="max-width: 130px">
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
    banks: [
      { src: '/images/home/banks/Banesco.png' },
      { src: '/images/home/banks/Mercantil.png' },
      { src: '/images/home/banks/Provincial.png' },
      { src: '/images/home/banks/Veezuela.png' },
      { src: '/images/home/banks/BOD.png' },
      { src: '/images/home/banks/BNC.png' },
      { src: '/images/home/banks/Banplus.png' },
      { src: '/images/home/banks/Bancaribe.png' },
      { src: '/images/home/banks/Bicentenario.png' }
    ]
  }),
  computed: {
    chunkedBanks() {
      const original = this.banks.slice()
      let items = this.banks.slice()
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
    &.available-banks {
      .v-carousel__next,
      .v-carousel__prev {
        top: 10px;
        width: 200px;
      }
    }
  }
}
</style>
