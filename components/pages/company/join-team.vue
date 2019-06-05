<template>
  <v-container class="main-container my-4">
    <v-layout>
      <v-container>
        <v-layout>
          <v-flex xs12 sm4>
            <div class="mb-3">
              <router-link to="/">
                <img src="/images/valiu-logo.png" width="50px">
              </router-link>
            </div>
            <h2 class="top-title text-primary font-size-2-3 mb-1">
              ¿Quieres ser<br /> parte de nuestro <br /> equipo?
            </h2>
          </v-flex>
          <v-flex xs12 sm8>
            <v-layout>
              <v-flex xs12 sm6 px-1 v-for="(item, index) in items" :key="index">
                <div class="join-team-item">
                  <v-layout>
                    <v-flex style="max-width: 60px;">
                      <img src="/images/company/linkedin.png" width="40px">
                    </v-flex>
                    <v-flex>
                      <div class="join-team-item-title">
                        {{ item.title }}
                      </div>
                      <div>
                        {{ item.country }}
                      </div>
                    </v-flex>
                  </v-layout>
                </div>
              </v-flex>
            </v-layout>
            <v-layout>
              <v-flex xs12>
                <div class="country-items pt-3">
                  <span
                    class="country-item"
                    :class="{active: country === activeCountry}"
                    v-for="(country, index) in countries"
                    :key="index">
                    {{ country }}
                  </span>
                </div>
              </v-flex>
            </v-layout>
          </v-flex>
        </v-layout>
      </v-container>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: [
      { title: 'Operations Trader', country: 'Bogotá' },
      { title: 'Country Manager', country: 'Ecuador' }
    ],
    activeCountry: 'All',
    countries: ['All', 'Colombia', 'Ecuador']
  })
}
</script>

<style lang="scss" scoped>
.main-container {
  padding: 4rem 0;
  background: #f4f8fe;
  border-radius: 40px;
  .top-title {
    font-weight: 900;
    letter-spacing: -1.2px;
    line-height: 35px;
  }
  .join-team-item {
    padding: 3rem;
    background: #fff;
    border-radius: 30px;
    box-shadow: 0 12px 28px 6px rgba(215, 224, 239, 0.49);
      &-title {
      top: -4px;
      color: #90a1b8;
      font-size: 22px;
      font-weight: 900;
      position: relative;
      letter-spacing: -0.86px;
    }
  }
  .country-items {
    .country-item {
      height: 30px;
      color: #90a1b8;
      cursor: pointer;
      background: #fff;
      margin-right: 10px;
      border-radius: 20px;
      padding: .5rem 1rem;
      &:not(.active) {
        box-shadow: 0 12px 28px 6px rgba(215, 224, 239, 0.49);
      }
      &.active {
        color: #fff;
        background: #354964;
      }
    }
  }
}
</style>
