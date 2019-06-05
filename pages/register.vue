<template>
  <div class="main-container register-container pt-5">
    <v-container pt-5>
      <v-layout wrap row>
        <v-flex sm12 md6 lg5 order-md2>
          <div class="hidden-md-and-up text-xs-center mb-3">
            <router-link to="/">
              <img src="/images/valiu-logo-white.png">
            </router-link>
          </div>
          <div class="register-wrapper px-4" style="max-width: 550px; margin: 0 auto">
            <div class="register-container box-shadow">
              <h2 class="top-title font-size-2-3 mb-4">
                Regístrate <br /> en Valiu ahora
              </h2>
              <div>
                <v-form>
                  <v-container px-0>
                    <v-layout row wrap>
                      <v-flex xs12 py-0 class="field-label">
                        Número de teléfono
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

                      <v-flex xs12 py-0 class="field-label">
                        Nombre Completo
                      </v-flex>
                      <v-flex xs12 py-0 mb-3>
                        <v-text-field
                          class="pt-0"
                          color="#007774"
                          placeholder="Tu nombre"
                        ></v-text-field>
                      </v-flex>

                      <v-flex xs12 py-0 class="field-label">
                        Email
                      </v-flex>
                      <v-flex xs12 py-0 mb-3>
                        <v-text-field
                          class="pt-0"
                          color="#007774"
                          placeholder="tuemail@ejemplo.com"
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
                        <v-btn depressed block class="text-capitalize submit-btn rounded-8">
                          Regístrate
                        </v-btn>
                      </v-flex>

                    </v-layout>
                  </v-container>
                </v-form>
              </div>
            </div>
            <div class="text-xs-center bottom-text">
              <span class="main-title">¿Ya tienes una cuenta?</span>
              <router-link class="sub-title ml-2" to="/login">Inicia Sesión</router-link>
            </div>
          </div>
        </v-flex>
        <v-flex sm12 md6 lg4 offset-lg1 order-md1>
          <v-layout wrap>
            <v-flex pl-3 mb-4 class="hidden-md-and-down">
              <div style="padding-left: 40px">
                <router-link to="/">
                  <img src="/images/valiu-logo-white.png">
                </router-link>
              </div>
            </v-flex>
            <v-flex v-for="(row, index) in items" :key="index" sm12 mb-4>
              <v-layout class="text-white about-container">
                <v-flex style="max-width: 40px">
                  <img src="/images/register/right.png" width="40px">
                </v-flex>
                <v-flex>
                  <div class="px-3">
                    <div class="font-size-1-3 item-title font-weight-bold">
                      {{ row.title }}
                    </div>
                    <div class="description item-description pr-5">
                      {{ row.description }}
                    </div>
                  </div>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>
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
    data: {},
    codes: [
      { code: '+57', country: 'Colombia', flag: '🇨🇴' },
      { code: '+593', country: 'Ecuador', flag: '🇪🇨' },
      { code: '+51', country: 'Perú', flag: '🇵🇪' },
      { code: '+56', country: 'Chile', flag: '🇨🇱' }
    ],
    items: [
      { title: 'Registro sencillo', description: 'Danos tu teléfono, tu nombre y un email para entrar en contacto contigo' },
      { title: 'Plataforma simple', description: 'Recibe pagos desde un computador o un smartphone.' },
      { title: 'Comienza a aceptar pagos', description: 'Recibe pagos desde un computador o un smartphone.' }
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
.register-container {
  &.main-container {
    max-height: 550px;
    border-radius: 0 0 70px 70px;
    background-image: linear-gradient(to right, #29c4a2 0%, #6ef4a3 98%);
    .description {
      color: #9be3d1;
    }
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
      .v-input__append-inner {
        .v-icon {
          color: #007774;
          font-size: 2rem !important;
        }
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
      padding-top: 150px;
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
        padding: 3rem 3rem 1.5rem;
      }
      .top-title {
        margin-bottom: 0 !important;
      }
      .about-container {
        padding-top: 40px;
        .item-title {
          color: #007774 !important;
        }
        .item-description {
          color: #9be3d1 !important;
        }
      }
    }
  }
}
</style>
