<template>
  <v-container class="main-container calulate-transfer-container py-0">
    <v-layout class="calulate-transfer-wrapper" wrap>
      <v-flex md6 lg4 class="caculation-wrapper" py-5>
        <div class="mb-4">
          <h2 class="top-title mb-3 font-size-2">
            Calcula <br />tu transferencia
          </h2>
        </div>
        <div>
          <v-layout wrap row>
            <v-flex xs12>
              <v-select
                :items="countries"
                placeholder="Country"
                v-model="data.country"
                @change="onCahangeCountry"
                :menu-props="{minWidth: '250px', offsetY: true}"
                append-icon="expand_more">
                <template slot="prepend-inner">
                  <span class="mr-3">Desde</span>
                </template>
                <template slot="selection" slot-scope="{ item }">
                  <div style="width: 100%;">
                    <span>{{ item.text }}</span>
                    <span class="float-right">
                      {{ item.flag }}
                    </span>
                  </div>
                </template>
                <template slot="item" slot-scope="{ item }">
                  <div style="width: 100%;">
                    <span>{{ item.text }}</span>
                    <span class="float-right">
                      {{ item.flag }}
                    </span>
                  </div>
                </template>
              </v-select>
            </v-flex>

            <v-flex xs12>
              <v-select
                :items="banks"
                v-model="data.bank"
                placeholder="Country"
                :menu-props="{minWidth: '250px', offsetY: true}"
                append-icon="expand_more">
                <template slot="prepend-inner">
                  <span class="mr-3">Banco</span>
                </template>
                <template slot="selection" slot-scope="{ item }">
                  <div style="width: 100%;">
                    <span>{{ item.text }}</span>
                    <span class="float-right">
                      {{ item.flag }}
                    </span>
                  </div>
                </template>
              </v-select>
            </v-flex>

            <v-flex xs12>
              <v-layout>
                <v-flex xs3>
                  <v-text-field
                    v-model="data.amount"
                    placeholder="$10,000"
                  ></v-text-field>
                </v-flex>
                <v-flex xs9>
                  <v-select
                    :items="currencies"
                    placeholder="Currency"
                    v-model="data.currency"
                    append-icon="expand_more"
                    @change="onCahangeCurrency"
                    :menu-props="{minWidth: '250px', offsetY: true}"
                    class="has-prefix-title">
                    <template slot="selection" slot-scope="{ item }">
                      <div style="width: 100%;">
                        <span>{{ item.value }}</span>
                        <span class="float-right">
                          {{ item.text }}
                        </span>
                      </div>
                    </template>
                  </v-select>
                </v-flex>
              </v-layout>
            </v-flex>

            <v-flex xs12>
              <v-layout>
                <v-flex xs3>
                  <v-text-field
                    v-model="data.conversion"
                    placeholder="10,800"
                  ></v-text-field>
                </v-flex>
                <v-flex xs9>
                  <v-select
                    :items="destinations"
                    placeholder="Currency"
                    v-model="data.destiny"
                    append-icon="expand_more"
                    @change="onCahangeCurrency"
                    :menu-props="{minWidth: '250px', offsetY: true}"
                    class="has-prefix-title">
                    <template slot="selection" slot-scope="{ item }">
                      <div style="width: 100%;">
                        <span>{{ item.value }}</span>
                        <span class="float-right">
                          {{ item.text }}
                        </span>
                      </div>
                    </template>
                  </v-select>
                </v-flex>
              </v-layout>
            </v-flex>
          </v-layout>

          <div class="mt-3">
            <v-btn depressed block color="primary" class="text-capitalize submit-btn rounded-8">
              Enviar
            </v-btn>
          </div>
        </div>
      </v-flex>
      <v-flex pl-5 mb-5>
        <div class="map-container pt-5">
          <div class="search-container clearfix">
            <div class="icon-container">
              <v-icon>search</v-icon>
            </div>
            <div class="input-container">
              <input type="text" placeholder="Busca un punto cercano a ti" name="">
            </div>
          </div>
          </v-text-field>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  props: {
    isTellersPage: {
      type: Boolean,
      default: false
    }
  },
  data: () => ({
    data: {
      bank: '0105',
      country: 'CO',
      currency: 'COP',
      destiny: 'VES'
    },
    countries: [
      { value: 'CO', text: 'Colombia', currency: 'COP', flag: '🇨🇴' },
      { value: 'EC', text: 'Ecuador', currency: 'ECS', flag: '🇪🇨' }
    ],
    banks: [
      { value: '0175', text: 'BANCO BICENTENARIO' },
      { value: '0102', text: 'BANCO DE VENEZUELA S.A.I.C.A.' },
      { value: '0114', text: 'BANCO DEL CARIBE C.A.' },
      { value: '0105', text: 'BANCO MERCANTIL C.A.' },
      { value: '0191', text: 'BANCO NACIONAL DE CREDITO' },
      { value: '0116', text: 'BANCO OCCIDENTAL DE DESCUENTO.' },
      { value: '0108', text: 'BANCO PROVINCIAL BBVA' },
      { value: '0134', text: 'BANESCO BANCO UNIVERSAL' },
      { value: '0174', text: 'BANPLUS BANCO COMERCIAL C.A' }
    ],
    currencies: [
      { value: 'COP', text: 'Peso Colombiano', country: 'CO' },
      { value: 'ECS', text: 'Dólar Ecuatoriano', country: 'EC' }
    ],
    destinations: [
      { value: 'VES', text: 'Bolívares', country: 'VES' }
    ]
  }),
  methods: {
    onCahangeCountry(country) {
      const row = this.currencies.find(row => row.country === country)
      this.data.currency = row.value
    },
    onCahangeCurrency(currency) {
      const row = this.countries.find(row => row.currency === currency)
      this.data.country = row.value
    }
  }
}
</script>

<style lang="scss">
.calulate-transfer-container {
  &.main-container {
    margin-top: 80px;
    border-radius: 40px;
    background: #f5f9fc;
    margin-bottom: 100px;
    .calulate-transfer-wrapper {
      padding: 0 75px;
      @media (max-width: 870px) {
        padding: 0 30px;
      }
    }
    padding: 4rem 0;
    .caculation-wrapper {
      top: -75px;
      background: #fff;
      position: relative;
      border-radius: 30px;
      padding: 3.5rem 2rem;
      box-shadow: 0 2px 50px #eef2f8;
      @media (min-width: 960px) {
        min-width: 380px;
      }
      .top-title {
        font-weight: 900;
        line-height: 40px;
        letter-spacing: -1.33px;
      }
      .v-input__prepend-inner {
        top: 3px;
        color: #354964;
        position: relative;
      }
      .has-prefix-title {
        .v-input__prepend-inner {
          color: #90a1b8;
        }
        .v-select__selections {
          .float-right {
            color: #009ce5;
            font-weight: 300;
            letter-spacing: -0.92px;
          }
        }
      }
      .v-select__selections {
        color: #90a1b8;
      }
      ::placeholder {
        color: #90a1b8;
        opacity: 1;
      }
      :-ms-input-placeholder {
        color: #90a1b8;
      }
      ::-ms-input-placeholder {
        color: #90a1b8;
      }
      .v-input__append-inner {
        .v-icon {
          color: #009ce5;
          font-size: 2rem !important;
        }
      }
      .submit-btn {
        min-height: 45px;
      }
    }
    .map-container {
      .search-container {
        background: #fff;
        border-radius: 10px;
        ::placeholder {
          color: #90a1b8;
          opacity: 1;
        }
        :-ms-input-placeholder {
          color: #90a1b8;
        }
        ::-ms-input-placeholder {
          color: #90a1b8;
        }
        .icon-container {
          width: 30px;
          float: left;
          padding: 12px 15px;
          .v-icon {
            color: #90a1b8;
          }
        }
        .input-container {
          float: left;
          width: calc(100% - 30px);
          input {
            width: 100%;
            padding: 15px 15px;
            &:focus {
              outline: none;
            }
          }
        }
      }
    }
  }
}
</style>
