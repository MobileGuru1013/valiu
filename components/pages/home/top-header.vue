<template>
  <v-container grid-list-md pt-5>
    <v-layout
      row
      pt-5
      wrap
      align-center
      align-content-center
      fill-height>
      <v-flex md6 text-xs-left>
        <h1 class="text-primary font-weight-bold header-title">Envía dinero<br/>a Venezuela</h1>
        <v-btn depressed color="primary" to="/register" class="mt-3 mx-0 text-capitalize register-btn rounded-10">
          Regístrate y envía
        </v-btn>
      </v-flex>
      <v-flex xs6 px-4 px-5 class="hidden-sm-and-down">
        <img src="/images/earth.png" width="70%">
      </v-flex>
    </v-layout>
  </v-container>
</template>

<style lang="scss" scoped>
.header-title {
  font-size: 50px;
  font-weight: 900;
  line-height: 60px;
  letter-spacing: -3.33px;
}
.register-btn {
  background-color: #009ce5;
  font-size: 1.1rem !important;
  box-shadow: 0 20px 40px #9dc9ff;
  padding: 1.6rem 2.5rem !important;
}
</style>
