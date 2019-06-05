<template>
  <div class="main-container login-container pt-5">
    <v-container pt-5>
      <v-layout row>
        <v-flex md8 offset-md2 lg6 offset-lg3>
          <div class="text-xs-center logo-wrapper mb-5">
            <router-link to="/">
              <img src="/images/valiu-logo-white.png">
            </router-link>
          </div>
          <div class="register-wrapper px-4">
            <div class="register-container box-shadow">
              <h2 class="top-title font-size-2-3 mb-4">
                <span v-if="verifyOtp">
                  Escribe el código <br />que te enviamos
                </span>
                <span v-else>
                  Iniciar Sesión
                </span>
              </h2>
              <div class="panel-sub-title" v-if="verifyOtp">
                Te enviamos un código de 4 dígitos a al {{ data.code }} {{ data.phone }}
              </div>
              <div>
                <v-form @submit.prevent lazy-validation>
                  <v-container px-0>
                    <v-layout row wrap>
                      <v-flex xs12 py-0 class="field-label">
                        <span v-if="verifyOtp">
                          Escríbe el código de 4 dígitos
                        </span>
                        <span v-else>
                          Número de teléfono
                        </span>
                      </v-flex>
                      <v-flex xs3 py-0 mb-3>
                        <v-select
                          class="pt-0"
                          color="#007774"
                          :items="codes"
                          placeholder="+57 CO"
                          v-model="data.code"
                          :menu-props="{minWidth: '250px', offsetY: true}"
                          append-icon="expand_more">
                          <template slot="selection" slot-scope="{ item }">
                            <div style="width: 100%;">
                              <span>{{ item.code }}</span>
                            </div>
                          </template>
                          <template slot="item" slot-scope="{ item }">
                            <div style="width: 100%;">
                              <span>{{ item.code }} {{ item.country }}</span>
                              <span class="float-right">
                                {{ item.flag }}
                              </span>
                            </div>
                          </template>
                        </v-select>
                      </v-flex>
                      <v-flex xs9 py-0 mb-3>
                        <v-text-field
                          class="pt-0"
                          color="#007774"
                          v-model="data.phone"
                          placeholder="(000) 000 00 00"
                        ></v-text-field>
                      </v-flex>
                      <v-flex xs12 py-0 mb-3>
                        <recaptcha
                          @error="onError"
                          @success="onVerify"
                          @expired="onExpired"
                        />
                      </v-flex>
                      <v-flex xs12 py-0 mb-3>
                        <v-btn
                          block
                          depressed
                          type="submit"
                          class="text-capitalize submit-btn rounded-8"
                          @click.native.prevent="onSubmit">
                          Entrar
                        </v-btn>
                      </v-flex>
                    </v-layout>
                  </v-container>
                </v-form>
              </div>
            </div>
            <div class="text-xs-center bottom-text">
              <span class="main-title">¿No tienes una cuenta?</span>
              <router-link class="sub-title ml-2" to="/register">Registrarme</router-link>
            </div>
          </div>
        </v-flex>
      </v-layout>
      <v-layout>
        <v-flex>
          <div class="text-xs-center footer">
            Valiu INC © Copyright 2019  All rights reserved
          </div>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>

<script>
/* eslint-disable */
export default {
  data: () => ({
    verifyOtp: false,
    data: {},
    codes: [
      { code: '+57', country: 'Colombia', flag: '🇨🇴' },
      { code: '+593', country: 'Ecuador', flag: '🇪🇨' },
      { code: '+51', country: 'Perú', flag: '🇵🇪' },
      { code: '+56', country: 'Chile', flag: '🇨🇱' }
    ]
  }),
  async mounted() {
    await this.$recaptcha.init()
    // await this.$recaptcha.init()
    // console.log(this.$recaptcha.siteKey)
  },
  methods: {
    onVerify() {
      console.log('onVerify')
      //
    },
    onError() {
      console.log('onError')
      //
    },
    onExpired() {
      console.log('onExpired')
      //
    },
    async onSubmit() {
      console.log('onSubmit')
      try {
        const token = await this.$recaptcha.getResponse()
        console.log('token', token)
      } catch (e) {
        console.log(e)
      }
    }
  }
}
</script>

<style lang="scss">
.login-container {
  &.main-container {
    max-height: 450px;
    border-radius: 0 0 70px 70px;
    background-image: linear-gradient(to right, #29c4a2 0%, #6ef4a3 98%);
    .description {
      color: #9be3d1;
    }
    .register-wrapper {
      .register-container {
        background: #fff;
        padding: 4rem 3.5rem 1.5rem;
        border-radius: 40px;
        .top-title {
          color: #007774;
          font-weight: 900;
          letter-spacing: -1.33px;
          line-height: 45px;
        }
        .field-label {
          color: #007774;
          font-size: 16px;
          font-weight: 300;
          letter-spacing: -0.67px;
        }
        .panel-sub-title {
          color: #007774;
          font-size: 26px;
          font-weight: 300;
          letter-spacing: -0.83px;
        }
        ::placeholder {
          color: rgba(0, 119, 116, 0.25);
          opacity: 1;
        }
        :-ms-input-placeholder {
          color: rgba(0, 119, 116, 0.25);
        }
        ::-ms-input-placeholder {
          color: rgba(0, 119, 116, 0.25);
        }
        .submit-btn {
          color: #fff;
          min-height: 50px;
          background: #007774 !important;
        }
      }
      .v-select__selections {
        // color: #009ce5;
      }
      .v-input__append-inner {
        .v-icon {
          color: #007774;
          font-size: 2rem !important;
        }
      }
    }
    .bottom-text {
      padding-top: 3rem;
      .main-title {
        color: #007774;
        font-size: 16px;
        font-weight: 500;
        letter-spacing: -0.67px;
      }
      .sub-title {
        color: #29c4a2;
        font-size: 16px;
        font-weight: 500;
        text-decoration: none;
        letter-spacing: -0.67px;
      }
    }
    .footer {
      color: #a2abb8;
      font-size: 15px;
      font-weight: 300;
      padding-top: 100px;
      letter-spacing: -0.58px;
    }
    @media (max-width: 768px) {
      padding-top: 0 !important;
      .logo-wrapper {
        margin-bottom: 1rem !important;
      }
      .container {
        padding-top: 2rem !important;
      }
      .register-wrapper {
        padding: 0 !important;
      }
      .footer {
        padding-top: 2rem;
      }
      .register-container {
        padding: 2rem 2rem 1.5rem;
      }
      .top-title {
        margin-bottom: 0 !important;
      }
    }
  }
}
</style>
