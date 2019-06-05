<template>
  <v-container grid-list-md class="text-xs-center">
    <h2 class="top-title font-size-2 mb-2">
      ¿Por qué Valiu?
    </h2>
    <v-layout
      row
      wrap
      align-space-around
      justify-center
      fill-height
      class="items-container pt-5">
      <v-flex
        v-for="(item, index) in items"
        :key="index"
        xs12
        md4
        lg4
        mb-5
        pt-4>
        <div class="item-container">
          <div class="avatar-container">
            <img :src="item.avatar">
          </div>
          <div class="px-3">
            <div class="main-title font-size-1-6 mb-2 px-2 font-weight-bold" v-html="item.title"></div>
            <div class="description text-muted">{{ item.description }}</div>
          </div>
        </div>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    items: [
      {
        title: 'Los usuarios no<br /> necesitan banco',
        description: 'Los usuarios pagan en nuestras tiendas de barrio (Tellers) para enviar el dinero.',
        avatar: '/images/company/why-us/bank.png'
      }, {
        title: 'Mejores tasas de<br /> cambio',
        description: 'Cobramos 5x veces menos que los competidores..',
        avatar: '/images/company/why-us/exchange.png'
      }, {
        title: 'Transferencias<br /> hechas el mísmo día',
        description: 'Nuestra transferencia promedio es de 1hr 30min.',
        avatar: '/images/company/why-us/transfers.png'
      }
    ]
  })
}
</script>

<style lang="scss" scoped>
.items-container {
  .item-container {
    background: #fff;
    min-height: 200px;
    position: relative;
    border-radius: 30px;
    height: 100%;
    padding: 50px 1.5rem 1.5rem;
    box-shadow: 0 12px 28px 6px rgba(215, 224, 239, 0.49);
    .text-muted {
      color: #90a1b8;
    }
    .avatar-container {
      top: -40px;
      width: 80px;
      height: 80px;
      margin: 0 auto;
      overflow: hidden;
      position: absolute;
      border-radius: 30px;
      left: calc(50% - 40px);
      img {
        width: 100%;
      }
    }
    @media (max-width: 1263px) {
      .main-title {
        font-size: 1.2rem;
      }
    }
  }
}
</style>
