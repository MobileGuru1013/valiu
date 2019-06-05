<template>
  <v-container grid-list-md class="main-container statistics-wrapper my-4">
    <v-layout>
      <v-container>
        <v-layout class="items-container" row wrap align-center align-content-start>
          <v-flex v-for="(row, index) in team" :key="index" class="py-4 item-container" sm6 md3>
            <v-layout>
              <v-flex class="avatar-container">
                <img :src="row.avatar" width="65px">
              </v-flex>
              <v-flex class="content-container">
                <div class="text-white px-3">
                  <div class="font-size-1-5 font-weight-bold">
                    {{ row.count }}
                  </div>
                  <div class="pr-5 description">
                    {{ row.title }}
                  </div>
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
    team: [
      { count: '12', title: 'Ciudades operando', avatar: '/images/company/statistics/location.png' },
      { count: '+300', title: 'Millones de pesos enviados', avatar: '/images/company/statistics/money.png' },
      { count: '+5000', title: 'Transferencias completadas', avatar: '/images/company/statistics/correct.png' },
      { count: '41', title: 'Tellers trabajando', avatar: '/images/company/statistics/users.png' }
    ]
  })
}
</script>

<style lang="scss">
.statistics-wrapper {
  &.main-container {
    padding: 4rem 0;
    background: #90a1b8;
    border-radius: 40px;
    img {
      border-radius: 17px;
      box-shadow: 0 12px 20px 0px rgba(55, 64, 79, 0.49);
    }
    .avatar-container {
      max-width: 65px;
    }
    @media (max-width: 600px) {
      padding: 2rem 0;
      .items-container {
        .item-container {
          flex-grow: 0 !important;
          max-width: 100% !important;
          flex-basis: 100% !important;
        }
        .layout {
          .avatar-container {
            max-width: 100%;
          }
          flex-wrap: wrap;
          text-align: center;
          .description,
          .content-container {
            flex-grow: 0 !important;
            max-width: 100% !important;
            flex-basis: 100% !important;
          }
        }
        .description {
          padding-right: 0 !important;
        }
      }
    }

  }
}
</style>
