<template>
  <div class="main-container">
    <v-container class="bg-container">
      <div class="sub-header-container text-xs-center">
        <div class="avatar-container">
          <img class="hidden-sm-and-down" src="/images/company/sub-header.png" width="100%">
          <img class="hidden-md-and-up" src="/images/company/sub-header-sm.png" width="100%" style="max-width: 550px">
        </div>
      </div>
      <v-layout row wrap px-2 class="content-container">
        <v-flex py-5 px-3 xs12 md6>
          <h2 class="top-title text-white">
            Aumentar el número de oportunidades en el mundo
          </h2>
        </v-flex>
        <v-flex py-5 px-3 xs12 md6>
          <p class="sub-content text-white font-size-1-5 pt-3 px-3">
            Valiu brinda oportunidades para que las personas envíen y reciban dinero. Nuestro objetivo es generar confianza con nuestros clientes al proporcionar una plataforma de remesas simple y transparente diseñada para sus verdaderas necesidades financieras.
          </p>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<style lang="scss" scoped>
.main-container {
  margin-bottom: 30px;
  .avatar-container {
    margin: 0 -30px;
  }
  .bg-container {
    top: -120px;
    min-height: 400px;
    position: relative;
    .top-title {
      font-size: 60px;
      font-weight: 900;
      line-height: 70px;
      letter-spacing: -1.71px;
    }
    .sub-content {
      font-weight: 300;
    }
    .sub-header-container {
      top: 0;
      left: 0;
      z-index: 0;
      width: 100%;
      height: 100%;
      position: absolute;
    }
    .layout {
      width: 80%;
      margin: 0 auto;
      position: relative;
    }
    .content-container {
      padding-top: 5rem;
    }
    @media (max-width: 1263px) {
      .top-title {
        font-size: 3rem;
        padding-top: 1rem;
        line-height: 50px;
      }
      .sub-content {
        font-size: 1rem;
      }
      .content-container {
        // padding-top: 0;
        .flex {
          padding: 0 !important;
        }
        .sub-content {
          font-size: 1.1rem;
          padding-top: 2rem !important;
          padding-left: 3rem !important;
        }
      }
    }
    @media (max-width: 960px) {
      .content-container {
        margin: 0 auto;
        max-width: 350px !important;
        .top-title {
          font-size: 2.2rem;
          padding-top: 1rem;
          line-height: 40px;
        }
        .sub-content {
          font-size: 1rem;
          padding: 0 !important;
          padding-top: 2rem !important;
        }
      }
    }
    // background: url(/images/company/sub-header.png) no-repeat center;
    // background-size: contain;
  }
}
</style>
