<template>
  <div>
    <div class="main-container">
      <v-container fluid px-0 py-0>
        <v-layout wrap row>
          <v-flex sm4 class="left-container">
            <v-layout>
              <v-flex offset-md4>
                <div class="pb-4 pt-5">
                  <img src="/images/valiu-logo.png" width="60px">
                </div>
                <ul class="terms-list">
                  <li
                    :key="index"
                    v-for="(term, index) in termsList"
                    class="terms-list-item">
                    {{ term.title }}
                    <ul class="terms-list-child">
                      <li
                        :key="index"
                        v-for="(childTerm, index) in term.children"
                        :class="{'active-item': activeTerm === childTerm.title}"
                        class="terms-list-child-item">
                        {{ childTerm.title }}
                      </li>
                    </ul>
                  </li>
                </ul>
              </v-flex>
            </v-layout>
          </v-flex>
          <v-flex sm8 class="right-container text-xs-right">
            <v-layout pt-4>
              <v-flex>
                <v-btn flat class="float-right mx-0">
                  <span class="font-size-1-2">
                    Ayuda
                  </span>
                </v-btn>
                <LanguageToggler left>
                  <template slot="label" slot-scope="{ on }">
                    <v-btn
                      class="float-right mx-0"
                      flat
                      v-on="on">
                      <span class="font-size-1-2">
                        <span>Idioma</span>
                        <v-icon>expand_more</v-icon>
                      </span>
                    </v-btn>
                  </template>
                </LanguageToggler>
              </v-flex>
            </v-layout>
          </v-flex>
        </v-layout>
      </v-container>
    </div>
    <HomeFooter />
  </div>
</template>
<script>
import HomeFooter from '@/components/pages/home/footer'
import LanguageToggler from '@@/components/language-toggler'
export default {
  components: {
    LanguageToggler,
    HomeFooter
  },
  data: () => ({
    activeTerm: 'Privacy policy',
    termsList: [
      { title: 'Valiu Services Agreement', children: [] },
      { title: 'Valiu Connect', children: [] },
      { title: 'Products and programs', children: [] },
      { title: 'Financial Services Terms', children: [] },
      { title: 'Payment Terms', children: [] },
      { title: 'Restricted Businesses', children: [] },
      {
        title: 'Privacy',
        children: [
          { title: 'Privacy policy' },
          { title: 'Cookies Policy' },
          { title: 'Data processing agreement' }
        ]
      },
      {
        title: 'Intellectual Property',
        children: [
          { title: '1. Privacy policy' },
          { title: '2. Cookies Policy' }
        ]
      }
    ]
  })
}
</script>

<style lang="scss">
.main-container {
  .left-container {
    background: #f4f8fe;
    .terms-list,
    .terms-list-child {
      margin: 0;
      padding: 0;
      text-align: left;
      line-height: 40px;
      &-item {
        font-size: 18px;
        list-style-type: none;
        letter-spacing: -0.67px;
      }
    }
    .terms-list {
      &-item {
        color: #354964;
        font-weight: 700;
      }
    }
    .terms-list-child {
      padding-left: 30px;
      &-item {
        color: #90a1b8;
        font-weight: 300;
        &.active-item {
          color: #009ce5;
        }
      }
    }
  }
}
</style>
