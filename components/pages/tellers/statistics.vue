<template>
  <v-container grid-list-md class="main-container my-4" fluid>
    <v-layout>
      <v-container>
        <v-layout row wrap align-center align-content-start>
          <v-flex v-for="(row, index) in items" :key="index" xs6 sm3>
            <v-layout>
              <v-flex style="max-width: 65px">
                <img class="statistics-icon" :src="row.avatar" width="65px">
              </v-flex>
              <v-flex>
                <div class="px-3">
                  <div class="font-size-1-5 font-weight-bold">
                    {{ row.count }}
                  </div>
                  <div class="pr-5">
                    {{ row.title }}
                  </div>
                </div>
              </v-flex>
            </v-layout>
          </v-flex>
          <v-flex px-0 pt-4>
            <div class="avatar-container">
              <img src="/images/tellers/tellers-avatar.png" width="100%">
              <div class="text-container">
                <div class="main-content">
                  “Sólo triunfa en el mundo quien se levanta y busca las circunstancias, y las crea si no las encuentra”
                </div>
                <div class="sub-content">George Bernard Shaw</div>
                <v-btn depressed to="/register" class="mt-5 mx-0 text-capitalize register-btn rounded-8">
                  Convertirme en Teller
                </v-btn>
              </div>
            </div>
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
      { count: '12', title: 'Ciudades operando', avatar: '/images/tellers/statistics/location.png' },
      { count: '+300', title: 'Millones de pesos enviados', avatar: '/images/tellers/statistics/money.png' },
      { count: '+5000', title: 'Transferencias completadas', avatar: '/images/tellers/statistics/correct.png' },
      { count: '41', title: 'Tellers trabajando', avatar: '/images/tellers/statistics/users.png' }
    ]
  })
}
</script>

<style lang="scss" scoped>
.main-container {
  padding: 4rem 0;
  background: #f0fdf5;
  max-height: 430px;
  margin-bottom: 330px !important;
  border-radius: 40px;
  color: #007774;
  .statistics-icon {
    border-radius: 17px;
  }
  .avatar-container {
    margin: 0 -1.3rem;
    position: relative;
    .text-container {
      top: 0;
      left: 0;
      z-index: 2;
      color: #fff;
      width: 100%;
      max-width: 60%;
      position: absolute;
      padding: 4.5rem 6rem;
      .main-content {
        font-size: 42px;
        font-weight: 300;
        line-height: 45px;
        margin-bottom: 20px;
        letter-spacing: -2.33px;
      }
      .sub-content {
        font-size: 20px;
        font-weight: 900;
        letter-spacing: -1.2px;
      }
      a {
        color: #fff;
        background: #29c4a2 !important;
      }
    }
  }
}
</style>
