<template>
  <v-container grid-list-md>
    <h1 class="text-xs-center top-header text-primary mb-4">
      Nuestros usuarios nos prefieren
    </h1>
      <TestimonialCarousel :items="items" chunk-items>
        <template slot="carousel-item" slot-scope="{ item }">
          <v-layout
            row
            wrap
            align-center
            class="testimonials-container pt-5"
            align-content-center>
            <v-flex
              xs12
              sm6
              px-2
              md4
              lg3
              mb-5
              :key="index"
              v-for="(row, index) in item"
              pt-4>
              <div class="testimonials-item">
                <div class="avatar-container text-xs-center">
                  <img :src="row.avatar">
                </div>
                <div class="quote-container">
                  <img src="/images/home/testimonials/quote.png">
                </div>
                <div class="user-name text-primary font-weight-bold">
                  {{ row.name }}
                </div>
                <div class="position-title font-weight-bold">
                  {{ row.position }}
                  <img :src="row.icon" class="float-right" width="20px">
                </div>
                <div class="testimonial-text">
                  {{ row.testimonial }}
                </div>
              </div>
            </v-flex>
          </v-layout>
        </template>
      </TestimonialCarousel>
    </v-layout>
  </v-container>
</template>

<script>
import TestimonialCarousel from '@@/components/testimonial-carousel'
export default {
  data: () => ({
    items: [
      {
        name: 'Andrea Solorzano',
        position: 'Envió para pagar Servicios',
        icon: '/images/home/testimonials/services.png',
        avatar: '/images/home/testimonials/andrea.png',
        testimonial: 'Me encanto la app, sobre todo el servicio al cliente. Gracias por ayudarme a enviar dinero a mi familia.'
      }, {
        name: 'Julian Pérez',
        position: 'Envió para pagar Comida',
        icon: '/images/home/testimonials/food.png',
        avatar: '/images/home/testimonials/julian.png',
        testimonial: 'Necesitaba enviar dinero para ayudar a mi familia a comprar comida y con Valiu fué posible.'
      }, {
        name: 'Gabriela Piñero',
        position: 'Envió para pagar Comida',
        icon: '/images/home/testimonials/food.png',
        avatar: '/images/home/testimonials/gabriela.png',
        testimonial: 'Sin duda la mejor tasa.. 100% recomendada, es excelente. El dinero le llegó a mí mamá súper rápido'
      }, {
        name: 'Jesús Marquez',
        position: 'Envió para pagar Servicios',
        icon: '/images/home/testimonials/services-2.png',
        avatar: '/images/home/testimonials/jesus.png',
        testimonial: 'En menos de 1 h ya mi papá tenia la plata en su cuenta en Venezuela y fue muy sencillo todo el proceso.'
      }, {
        name: 'Benjamín Sánchez',
        position: 'Envió para pagar medicinas',
        icon: '/images/home/testimonials/medicine.png',
        avatar: '/images/home/testimonials/benjamin.png',
        testimonial: 'Sin duda la mejor tasa.. 100% recomendada, es excelente. El dinero le llegó a mí mamá súper rápido'
      }, {
        name: 'Anabella Zannin',
        position: 'Envió para pagar servicios',
        icon: '/images/home/testimonials/mastercard.png',
        avatar: '/images/home/testimonials/anabella.png',
        testimonial: 'Excelente! El servicio mas rápido y eficiente para enviar dinero a venezuela 🔝 y pagar mi tarjeta de crédito.'
      }
    ]
  }),
  components: {
    TestimonialCarousel
  }
}
</script>

<style lang="scss">
.testimonials-container {
  .testimonials-item {
    background: #fff;
    position: relative;
    border-radius: 30px;
    padding: 80px 1.5rem 3rem;
    transition: transform 0.5s;
    box-shadow: 0 12px 28px 6px rgba(215, 224, 239, 0.49);
    &:hover {
      z-index: 1;
      transform: scale(1.1);
    }
    .user-name {
      font-size: 17px;
      font-weight: 900;
      margin-bottom: 2px;
      letter-spacing: -1px;
    }
    .position-title {
      color: #009ce5;
      font-size: 13px;
      font-weight: 700;
      letter-spacing: -0.91px;
    }
    .testimonial-text {
      color: #90a1b8;
      font-size: 11px;
      font-weight: 300;
      padding-top: 10px;
      letter-spacing: -1.01px;
    }
    .avatar-container {
      top: -60px;
      width: 120px;
      height: 120px;
      margin: 0 auto;
      overflow: hidden;
      position: absolute;
      background: #f5f9fc;
      border-radius: 30px;
      left: calc(50% - 60px);
      img {
        width: 100%;
      }
    }
    .quote-container {
      top: 30px;
      position: absolute;
      right: calc(50% - 70px);
    }
  }
}
</style>
