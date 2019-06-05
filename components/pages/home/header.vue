<template>
  <v-toolbar
    app
    flat
    absolute
    class="light"
    v-show="showHeader"
    :class="wrapperClasses">
    <v-toolbar-title>
      <router-link to="/">
        <img :src="logo" width="60px">
      </router-link>
    </v-toolbar-title>
    <v-spacer></v-spacer>
    <v-toolbar-items class="hidden-sm-and-down nav-actions">
      <!-- eslint-disable -->
      <LanguageToggler left>
        <template slot="label" slot-scope="{ on }">
          <v-btn
            flat
            @click.native.prevent.stop
            class="btn-idioma"
            v-on="on">
            <span>Idioma</span>
            <v-icon>expand_more</v-icon>
          </v-btn>
        </template>
      </LanguageToggler>
      <v-btn flat exact nuxt class="btn-home" small to="/">
        Home
      </v-btn>
      <TellersDropdown left>
        <template slot="label" slot-scope="{ on }">
          <v-btn
            flat
            @click.native.prevent.stop
            class="btn-tellers"
            v-on="on">
            <span>Tellers</span>
            <v-icon>expand_more</v-icon>
          </v-btn>
        </template>
      </TellersDropdown>
      <v-btn flat exact nuxt small class="btn-company" to="/company">
        Empresa
      </v-btn>
      <v-btn flat exact nuxt small class="btn-blog" to="/blog">
        Blog
      </v-btn>
      <v-btn flat exact nuxt small class="btn-ayuda" to="/ayuda">
        Ayuda
      </v-btn>
    </v-toolbar-items>
    <v-menu
      offset-y
      min-width="100%"
      :close-on-content-click="true">
      <template v-slot:activator="{ on }">
        <v-toolbar-side-icon  class="hidden-md-and-up" v-on="on"></v-toolbar-side-icon>
      </template>
      <v-list class="header-menu-xs nav-actions pl-2">
        <v-btn flat exact block nuxt class="btn-home" to="/">
          Home
        </v-btn>
        <v-btn flat block class="btn-tellers" @click="onClickTellers">
          <span>Tellers</span>
          <v-icon>expand_more</v-icon>
        </v-btn>
        <transition-group name="slide-fade">
          <template v-if="showTellers">
            <div
              class="pt-3 tellers-row-container"
              v-for="(row, index) in tellers"
              :key="index">
              <router-link 
                tag="div"
                :to="row.value"
                class="tellers-row pb-3 px-3"
                :class="{'teller-active': $route.path === row.value}">
                <span class="teller-lang">{{ row.value }}</span>
                <span class="teller-name">{{ row.name }}</span>
              </router-link>
              </div>
          </template>
        </transition-group>
        <v-btn flat exact block nuxt class="btn-company" to="/company">
          Empresa
        </v-btn>
        <v-btn flat exact block nuxt class="btn-blog" to="/blog">
          Blog
        </v-btn>
        <v-btn flat exact block nuxt class="btn-ayuda" to="/ayuda">
          Ayuda
        </v-btn>
        <v-btn flat block class="btn-home" @click="onClickLanguageSelector">
          <span>Idioma</span>
          <v-icon>expand_more</v-icon>
        </v-btn>
        <transition name="slide-fade">
          <template v-if="showLanguageSelectors">
            <div class="languages-toggler pt-3">
              <div
                v-for="(row, index) in languages"
                :key="index">
                <div class="language-row pb-3 px-3" :class="{'language-active': activeLanguage === row.lang}">
                  <span class="language-lang">{{ row.lang }}</span>
                  <span class="language-name">{{ row.name }}</span>
                </div>
              </div>
            </div>
          </template>
        </transition>
      </v-list>
    </v-menu>

  </v-toolbar>
</template>

<script>
import LanguageToggler from '@@/components/language-toggler'
import TellersDropdown from '@@/components/tellers-dropdown'
export default {
  data: () => ({
    showLanguageSelectors: false,
    showTellers: false,
    languages: [
      { name: 'Español', lang: 'es' },
      { name: 'English', lang: 'en' }
    ],
    activeLanguage: 'es',
    tellers: [
      { name: 'Convertirse En Un Cajero', value: '/tellers' },
      { name: 'Iniciar Sesión', value: '/login' },
      { name: 'Registrarme', value: '/register' }
    ]
  }),
  computed: {
    wrapperClasses() {
      return {
        'home-page': this.isHomePage,
        'company-page': this.isCompanyPage,
        'blog-page': this.isBlogPage
      }
    },
    isHomePage() {
      return this.$route.name === 'index'
    },
    isCompanyPage() {
      return this.$route.name === 'company'
    },
    isBlogPage() {
      return this.$route.name === 'blog'
    },
    isTellersPage() {
      return this.$route.name === 'tellers'
    },
    showHeader() {
      return this.isHomePage || this.isCompanyPage || this.isBlogPage || this.isTellersPage
    },
    logo() {
      return this.isBlogPage || this.isCompanyPage ? '/images/valiu-logo-white.png' : '/images/valiu-logo.png'
    }
  },
  methods: {
    onClickLanguageSelector() {
      this.showLanguageSelectors = !this.showLanguageSelectors
    },
    onClickTellers() {
      this.showTellers = !this.showTellers
    }
  },
  components: {
    LanguageToggler,
    TellersDropdown
  }
}
</script>

<style lang="scss">
.theme--light {
  &.v-toolbar {
    background: #fff !important;
  }
  &.company-page {
    background: #90a1b8 !important;
    background: #90a1b8 !important;
  }
  &.blog-page {
    background: transparent !important;
  }
}
.header-menu-xs {
  .v-btn__content {
    justify-content: left;
  }
  .languages-toggler {
    background: #f4f8fe;
  }
  .tellers-row-container {
    background: #eefffe;
    .teller-name {
      color: #17c5a2;
    }
  }
}
.nav-actions {
  .v-btn--flat {
    .v-btn__content {
      color: #354964;
    }
    .v-icon {
      color: #354964 !important;
    }
  }
}
nav {
  &.v-toolbar {
    // top: -64px !important;
    .v-toolbar__content {
      width: 100%;
      margin: auto;
      padding: 24px;
      flex: 1 1 100%;
      .v-toolbar__side-icon {
        .v-icon {
          color: #354964 !important;
        }
      }
      @media only screen and (min-width: 960px) {
        & {
          max-width: 900px;
        }
      }
      @media only screen and (min-width: 1264px) {
        & {
          max-width: 1185px;
        }
      }
      @media only screen and (min-width: 1904px) {
        & {
          max-width: 1520px !important;
        }
      }
      @media only screen and (max-width: 959px) {
        & {
          padding: 16px;
        }
      }
    }
  }
  &.company-page,
  &.blog-page {
    .v-btn--flat {
      .v-btn__content {
        color: #fff;
        .v-icon {
          color: #fff !important;
        }
      }
    }
  }
  &.home-page {
    .nav-actions {
      .v-btn--flat {
        &.btn-idioma:hover {
          .v-btn__content {
            color: #91a2b8;
          }
          .v-icon {
            color: #91a2b8 !important;
          }
        }
        &.btn-home:hover {
          .v-btn__content {
            color: #009ce5;
          }
        }
        &.btn-tellers:hover {
          .v-btn__content {
            color: #007774;
          }
          .v-icon {
            color: #007774 !important;
          }
        }
        &.btn-company:hover {
          .v-btn__content {
            color: #91a2b8;
          }
        }
        &.btn-blog:hover {
          .v-btn__content {
            color: #0059ff;
          }
        }
        &.btn-ayuda:hover {
          .v-btn__content {
            color: #6a56ff;
          }
        }
      }
    }
  }
}
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .5s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}
</style>
