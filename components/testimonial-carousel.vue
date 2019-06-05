<template>
  <v-carousel
    height
    :cycle="false"
    hide-controls
    class="how-works-slider"
    delimiter-icon="stop">
    <v-carousel-item
      v-for="(item, index) in getFinalItems"
      :key="index">
      <slot name="carousel-item" :item="item" />
    </v-carousel-item>
  </v-carousel>
</template>

<script>
import $ from 'jquery'
export default {
  props: {
    items: {
      type: Array,
      required: true
    },
    chunkItems: {
      type: Boolean,
      default: false
    },
    breakPoints: {
      type: Object,
      default: () => ({
        minLarge: 4,
        minMedium: 4,
        minSmall: 3,
        minXSmall: 2,
        maxXSmall: 1
      })
    }
  },
  data: () => ({
    chunk: 4,
    __setChunkTimeOut: null,
    breaks: {
      minLarge: 1904,
      minMedium: 1264,
      minSmall: 960,
      minXSmall: 600,
      maxXSmall: 600
    }
  }),
  computed: {
    getFinalItems() {
      return this.chunkItems ? this.getChunkedItems() : this.items
    }
  },
  methods: {
    getChunkedItems() {
      const original = this.items.slice()
      let items = this.items.slice()
      items = [].concat.apply([], items.map((el, i) => i % this.chunk ? [] : [items.slice(i, i + this.chunk)]))
      const last = items.slice().pop()
      if (last.length !== this.chunk) {
        items[items.length - 1] = last.concat(original.slice(0, this.chunk - last.length))
      }
      return items
    },
    setChunkBasedOnWindowWidth() {
      clearTimeout(this.__setChunkTimeOut)
      this.__setChunkTimeOut = setTimeout(() => {
        const width = $(window).outerWidth()
        let chunked = false
        Object.entries(this.breaks).map(([key, value]) => {
          if (!chunked && this.breakPoints[key]) {
            if (key.substring(0, 3) === 'min' && width >= value) {
              this.chunk = this.breakPoints[key]
              chunked = true
            } else if (key.substring(0, 3) === 'max' && width <= value) {
              chunked = true
              this.chunk = this.breakPoints[key]
            }
          }
        })
      }, 50)
    }
  },
  mounted() {
    if (this.chunkItems) {
      this.setChunkBasedOnWindowWidth()
      $(window).resize(() => {
        this.setChunkBasedOnWindowWidth()
      })
    }
  }
}
</script>

<style lang="scss">
.v-window {
  &.v-carousel {
    &.how-works-slider {
      overflow: visible;
      .v-window-item {
        .v-carousel__item {
          overflow: inherit;
        }
      }
      .v-carousel__controls {
        padding-top: 50px;
        background: transparent;
        justify-content: flex-start;
        .v-item-group {
          .v-btn {
            width: 20px;
            margin: 0 !important;
            .v-btn__content {
              position: relative;
              &::before {
                content: '';
                width: 10px;
                height: 10px;
                display: block;
                border-radius: 5px;
                position: absolute;
                background: #90a1b8;
              }
              .v-icon {
                display: none;
              }
            }
            &.v-btn--active {
              width: 50px;
              .v-btn__content {
                &::before {
                  width: 30px;
                  background: #354964;
                }
              }
            }
          }
        }
      }
    }
  }
}
</style>
