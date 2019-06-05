<template>
  <v-container class="text-xs-center main-container">
    <div class="mb-4">
      <h1 class="top-title text-primary mb-1">
        ¿Cómo enviar con valiu?
      </h1>
      <p class="sub-title">
        Puedes descargar la app o escribirnos desde cualquier parte de Colombia o Ecuador<br />
        a nuestro canal de atención en Whatsapp
      </p>
    </div>
    <v-layout row wrap mb-2>
      <v-flex xs12 md6 class="pr-2 mb-4">
        <div class="app-stores">
          <div class="item-title mb-2">Descarga la app</div>
          <router-link to="/">
            <span class="store-download mr-4">
              <span class="fab fa-apple"></span>
            </span>
          </router-link>
          <router-link to="/">
            <span class="store-download google-play">
              <span class="fas fa-play"></span>
            </span>
          </router-link>
        </div>
      </v-flex>
      <v-flex xs12 md6 class="pl-2">
        <div class="whatsapp-contant">
          <div class="pt-3">
            <v-layout align-start justify-center row class="whatsapp-contant-wrapper">
              <v-flex xs2 style="max-width: 90px">
                <img src="/images/whatsapp-icon.png" width="60px">
              </v-flex>
              <v-flex xs2 class="text-xs-left">
                <div class="whatsapp-title ml-2">
                  Whatsapp<br/>
                  Corporativo
                </div>
              </v-flex>
            </v-layout>
          </div>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<style lang="scss" scoped>
.main-container {
  padding: 4rem 0;
  .sub-title {
    font-size: 0.95rem;
    letter-spacing: -0.5px;
  }
  .item-title {
    font-size: 22px;
    font-weight: 900;
    letter-spacing: -1px;
    line-height: 40.5px;
  }
  .whatsapp-contant {
    background: #eefffe;
    .whatsapp-title {
      font-size: 25px;
      font-weight: 900;
      line-height: 30px;
      letter-spacing: -1px;
    }
    .whatsapp-contant-wrapper {
      margin-left: -70px;
    }
  }
  .whatsapp-contant,
  .app-stores {
    padding: 3rem 0;
    min-height: 165px;
    border-radius: 40px;
  }
  .app-stores {
    background: #f2fafd;
    .store-download {
      color: #fff;
      width: 90px;
      height: 35px;
      line-height: 35px;
      font-size: 1.5rem;
      border-radius: 10px;
      display: inline-block;
      background: linear-gradient(180deg, #c3cfdd 0%, #90a1b8 100%);
      &.google-play {
        font-size: 1.1rem;
      }
      &:hover {
        background: linear-gradient(180deg, #c3cfdd 0%, #90a1b8 60%);
      }
    }
  }
}
</style>
