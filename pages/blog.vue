<template>
  <div class="blog-container">
    <div class="main-container pt-5">
      <v-container pt-5>
        <v-layout pt-5>
          <v-flex px-0>
            <div class="font-size-2 text-white">
              Blog
            </div>
          </v-flex>
          <v-flex lg3>
            <v-text-field
              color="#fff"
              label="Buscar"
              append-icon="search"
            ></v-text-field>
          </v-flex>
        </v-layout>
      </v-container>
    </div>

    <v-container class="content-container box-shadow">
      <div class="avatar-container">
        <img src="/images/blog/default-profile.jpg">
      </div>
      <v-layout row>
        <v-flex md8 offset-md2 lg6 offset-lg3>
          <div  style="height: 600px;"></div>
        </v-flex>
      </v-layout>
    </v-container>

    <v-container class="invests-container">
      <v-layout row>
        <v-flex md6 py-2 px-4>
          <div>
            <span class="notice-text">
              Noticias
            </span>
          </div>
          <h3 class="top-title text-white font-size-2">
            Valiu invierte en Latam
          </h3>
          <div class="description pt-4">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
            <div class="pt-4">
              Abril 15, 2019
            </div>
          </div>
        </v-flex>
      </v-layout>
    </v-container>

    <v-container class="invests-container invests-white-container">
      <v-layout row>
        <v-flex md4 style="max-width: 220px;">
          <div class="avatar-container"></div>
        </v-flex>
        <v-flex md6 py-2 px-4>
          <div>
            <span class="notice-text">
              Noticias
            </span>
          </div>
          <h3 class="top-title text-white font-size-2">
            Valiu invierte en Latam
          </h3>
          <div class="description pt-4">
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
            <div class="pt-4">
              Abril 15, 2019
            </div>
          </div>
        </v-flex>
      </v-layout>
    </v-container>

    <HomeFooter />
  </div>
</template>

<script>
import HomeFooter from '@/components/pages/home/footer'
// import VueRecaptcha from 'vue-recaptcha'
export default {
  components: {
    HomeFooter
  }
}
</script>

<style lang="scss">
.blog-container {
  .content-container {
    top: -230px;
    position: relative;
    background: #fff;
    padding: 4rem 3.5rem 1.5rem;
    border-radius: 40px;
    .avatar-container {
      top: -30px;
      position: absolute;
      left: calc(50% - 30px);
      img {
        width: 60px;
        height: 60px;
        border-radius: 50%;
      }
    }
  }
  .invests-container {
    border-radius: 40px;
    background: #009ce5;
    margin-bottom: 60px;
    padding: 4rem 3.5rem 1.5rem;
    box-shadow: 0 14px 35px 7px rgba(215, 224, 239, 0.49);
    .notice-text {
      color: #009ce5;
      font-size: 16px;
      font-weight: 900;
      background: #fff;
      padding: 5px 10px;
      border-radius: 6px;
      margin-bottom: 20px;
      display: inline-block;
      letter-spacing: -0.67px;
    }
    .top-title {
      font-weight: 900;
      letter-spacing: -1.2px;
    }
    .description {
      color: #fff;
      font-size: 16px;
      font-weight: 300;
      letter-spacing: -0.6px;
      line-height: 22px;
    }
    &.invests-white-container {
      background: #fff;
      .notice-text {
        color: #fff;
        background: #354964;
      }
      .top-title {
        color: #009ce5;
      }
      .description {
        color: #354964;
      }
      .avatar-container {
        width: 200px;
        height: 200px;
        background: #e9e9e9;
        border-radius: 15px;
      }
    }
  }
  .main-container {
    min-height: 500px;
    border-radius: 0 0 70px 70px;
    background-image: linear-gradient(135deg, #00bdff 0%, #0c6bcd 100%);
    .v-input {
      &.v-text-field {
        label {
          color: #fff;
        }
        .v-input__slot {
          &::before {
            border-color: #fff;
          }
        }
        &:hover {
          .v-input__slot {
            &::before {
              border-color: #fff !important;
            }
          }
        }
        .v-input__icon {
          i {
            color: #fff;
          }
        }
      }
    }
  }
}
</style>
