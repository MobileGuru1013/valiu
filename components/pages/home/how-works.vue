<template>
  <v-container px-0 class="how-works-container">
    <div class="mb-4">
      <h2 class="top-title mb-1 font-size-2-2 px-3">
        ¿Cómo funciona?
      </h2>
    </div>
    <TestimonialCarousel :items="items">
      <template slot="carousel-item" slot-scope="{ item }">
        <div class="main-container" :style="{background: item.color}">
          <v-layout>
            <v-flex sm4 offset-sm1 class="content-container">
              <v-layout wrap>
                <v-flex xs12>
                  <v-layout wrap align-center justify-center>
                    <v-flex md4 offset-md1 style="max-width: 65px;">
                      <img :src="item.icon" width="65px">
                    </v-flex>
                    <v-flex md8>
                      <h2 class="sub-title mb-1 font-size-2 px-3" v-html="item.title"></h2>
                    </v-flex>
                  </v-layout>
                </v-flex>
                <v-flex sm12 offset-md1>
                  <div class="description mt-3">
                    {{ item.description }}
                  </div>
                </v-flex>
              </v-layout>
            </v-flex>
            <v-flex sm4 offset-sm1 class="avatar-flex">
              <div class="avatar-container">
                <img :src="item.avatar" width="60%">
              </div>
            </v-flex>
          </v-layout>
        </div>
      </template>
    </TestimonialCarousel>
  </v-container>
</template>

<script>
import TestimonialCarousel from '@@/components/testimonial-carousel'
export default {
  data: () => ({
    items: [
      {
        color: '#f4f8fe',
        title: 'Crea <br /> una cuenta',
        avatar: '/images/home/how-works/create-an-account.png',
        icon: '/images/home/how-works/create-an-account-icon.png',
        description: 'Lo único que necesitas es un número de teléfono. Para descargar la aplicación, abre la App Store o Google Play.'
      }, {
        color: '#fdf5f5',
        title: 'Añade un <br /> Destinatario',
        avatar: '/images/home/how-works/address.png',
        icon: '/images/home/how-works/address-icon.png',
        description: 'Abre la aplicación para elegir el banco del receptor e ingresar su información personal.'
      }, {
        color: '#fef8e7',
        title: 'Descansa <br /> y relajate',
        avatar: '/images/home/how-works/rest-relax.png',
        icon: '/images/home/how-works/rest-relax-icon.png',
        description: 'Te enviaremos notificaciones por mensaje de texto una vez que llegue el dinero. También puedes consultar el estado de tu transferencia en la aplicación.'
      }, {
        color: '#eefffe',
        title: 'Paga en <br /> Efectivo',
        avatar: '/images/home/how-works/pay-cash.png',
        icon: '/images/home/how-works/pay-cash-icon.png',
        description: 'El pago es fácil. Tienes varias opciones dependiendo de tu región. Usa efectivo o transferencia bancaria.'
      }
    ]
  }),
  components: {
    TestimonialCarousel
  }
}
</script>

<style lang="scss">
.how-works-container {
  .main-container {
    padding: 10rem 0;
    background: #f4f8fe;
    border-radius: 40px;
    margin-bottom: 50px;
    @media (max-width: 768px) {
      padding: 4rem;
      .avatar-flex {
        display: none !important;
      }
      .content-container {
        flex-basis: 100%;
        flex-grow: 0;
        max-width: 100%;
        .layout {
          .layout {
            margin: 0 auto;
            max-width: 300px;
          }
        }
      }
    }
    .sub-title {
      color: #354964;
      font-weight: 700;
      line-height: 30px;
      letter-spacing: -1.33px;
    }
    .description {
      color: #90a1b8;
      font-weight: 400;
    }
    position: relative;
    .avatar-container {
      top: -7rem;
      right: -10rem;
      position: absolute;
    }
  }
}
</style>
