<template>
  <v-container grid-list-md pt-5>
    <v-layout row wrap align-content-center>
      <v-flex xs12 sm7 order-sm2 mb-4>
        <v-layout row align-content-center>
          <v-flex>
            <div class="text-primary font-weight-bold font-size-1-3">
              Empresa
            </div>
            <div class="footer-list">
              <router-link to="/">Trabajar en Valiu</router-link>
            </div>
          </v-flex>
          <v-flex>
            <div class="text-primary font-weight-bold font-size-1-3">
              Tellers
            </div>
            <div class="footer-list">
              <router-link to="/">Iniciar Sesión</router-link>
              <router-link to="/">Registrarme</router-link>
            </div>
          </v-flex>
          <v-flex>
            <div class="text-primary font-weight-bold font-size-1-3">
              Ayuda
            </div>
            <div class="footer-list">
              <router-link to="/">Preguntas</router-link>
              <router-link to="/">Frecuentes</router-link>
            </div>
          </v-flex>
          <v-flex>
            <div class="text-primary font-weight-bold font-size-1-3">
              Blog
            </div>
          </v-flex>
        </v-layout>
      </v-flex>
      <v-flex xs12 sm5 order-sm1 class="text-xs-center text-sm-left">
        <router-link to="/" class="mr-3">
          <img src="/images/valiu-logo.png" width="45px">
        </router-link>
        <div class="pt-3">
          <LanguageToggler footer-dropdown>
            <template slot="label" slot-scope="{ on }">
              <span v-on="on" class="cursor-pointer py-3">
                <span class="text-primary font-weight-bold font-size-1-3 mt-3">
                  Español
                </span>
                <v-icon class="text-primary-important">expand_more</v-icon>
              </span>
            </template>
          </LanguageToggler>
        </div>
        <div class="social-media-icons mt-5">
          <span class="fab fa-facebook-f mr-3"></span>
          <span class="fab fa-instagram mr-3"></span>
          <span class="fab fa-intercom mr-3"></span>
          <span class="fab fa-linkedin-in mr-3"></span>
        </div>
        <div class="terms-condictions mt-3">
          Términos y condiciones
        </div>
      </v-flex>
    </v-layout>
    <v-layout pt-3>
      <v-flex class="text-xs-center">
        <div class="copy-right mb-4 mt-1">
          © Copyright 2019 Valiu Inc. All rights reserved
        </div>
        <span class="privacy-policy-container rounded-8" v-if="hasPrivacyAndPolicy">
          <img src="/images/cake-footer.png" width="18px" class="mr-1">
          <span class="privacy-title">Al explorar nuestra web, consientes nuestra</span>
          <span class="privacy-policy">Política de privacidad</span>
          <v-btn depressed color="primary" to="/" class="mr-0 my-0 text-capitalize rounded-8">
            Acepto
          </v-btn>
        </span>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import LanguageToggler from '@@/components/language-toggler'
export default {
  props: {
    hasPrivacyAndPolicy: {
      type: Boolean,
      default: false
    }
  },
  components: {
    LanguageToggler
  }
}
</script>

<style lang="scss" scoped>
.social-media-icons {
  color: #3c3c3c;
}
.terms-condictions {
  color: #009ce5;
  font-weight: 300;
  letter-spacing: -1px;
  text-decoration: underline;
}
.copy-right {
  font-size: 0.7rem;
  font-weight: 300;
  letter-spacing: -0.67px;
}
.footer-list {
  padding-top: 1rem;
  a {
    display: block;
    font-weight: 300;
    margin-top: 0.6rem;
    letter-spacing: -1px;
    text-decoration: none;
  }
}
.privacy-policy-container {
  background: #fff;
  padding-left: 1.2rem;
  display: inline-block;
  .privacy-title {
    font-weight: 300;
    letter-spacing: -1px;
  }
  .privacy-policy {
    color: #009ce5;
    font-weight: 700;
  }
  img {
    top: 3px;
    position: relative;
  }
}
</style>
