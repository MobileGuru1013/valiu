<template>
  <v-container grid-list-md class="main-container my-4" fluid>
    <v-layout>
      <v-container>
        <v-layout row wrap align-center align-content-start>
          <v-flex px-0 pt-4>
            <div class="avatar-container">
              <img src="/images/tellers/tellers-register.png" width="100%">
              <div class="text-container">
                <h2 class="top-title text-white font-size-2-3 mb-4">
                  Registro <br /> sencillo
                </h2>
                <div class="sub-content">
                  Danos tu teléfono, tu nombre y un email para entrar en contacto contigo y así podrás comenzar a ganar dinero ya.
                </div>
                <v-btn depressed to="/register" class="mt-5 mx-0 px-5 text-capitalize rounded-5">
                  Regístrarme
                </v-btn>
              </div>
            </div>
          </v-flex>
        </v-layout>
      </v-container>
    </v-layout>
  </v-container>
</template>

<style lang="scss" scoped>
.main-container {
  .avatar-container {
    position: relative;
    .text-container {
      top: 0;
      left: 0;
      z-index: 2;
      color: #fff;
      width: 100%;
      position: absolute;
      padding: 4.5rem 6rem;
      padding-left: 60%;
      .top-title {
        line-height: 35px;
        letter-spacing: -1px;
      }
      .sub-content {
        font-size: 16px;
        font-weight: 300;
        letter-spacing: -1px;
      }
      a {
        color: #fff;
        background: #0e7e7b !important;
      }
    }
  }
}
</style>
