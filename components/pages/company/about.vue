<template>
  <v-container grid-list-md class="main-container">
    <div class="text-xs-center">
      <h2 class="top-title text-primary font-size-2 mb-2">
        ¿Quienes sómos?
      </h2>
      <p>Somos un equipo de emprendedores jóvenes que buscan cambiar la manera en que se mueve el dinero.</p>
    </div>
    <v-layout
      row
      wrap
      justify-between
      justify-space-between
      v-for="(items, index) in chunkedItems"
      :key="index">
      <v-flex
        v-for="(item, index) in items"
        :key="index"
        class="py-4"
        xs6
        sm3
        style="width: 160px; max-width: 160px">
        <div class="px-1">
          <img :src="item.avatar" width="160px">
        </div>
        <div class="text-xs-center" style="width: 160px">
          <div class="text-primary font-size-1-3 font-weight-bold pt-2">
            {{ item.name }}
          </div>
          <div>
            {{ item.position }}
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
      { name: 'David Barinas', position: 'Co-founder & CTO', avatar: '/images/company/team/IMG_9931.png' },
      { name: 'Simón Chamorro', position: 'Co-founder & CEO', avatar: '/images/company/team/headhot@2x.png' },
      { name: 'Gabriel Ascanio', position: 'Co-founder & COO', avatar: '/images/company/team/s0@2x.png' },
      { name: 'Alberto Niego', position: 'VP of product', avatar: '/images/company/team/2@2x.png' },
      { name: 'Rafael De Guglielmo', position: 'Founding Partner & Head of Design', avatar: '/images/company/team/WhatsApp_Image_2018-10-16_at_10.31.48_AM@2x.png' },
      { name: 'Julian Pérez', position: 'Head of Operations', avatar: '/images/company/team/0@2x.png' },
      { name: 'Juan Peña', position: 'Head of Tellers Acquisition', avatar: '/images/company/team/IMG_9035@2x.png' },
      { name: 'Luis Córdoba', position: 'Operations Trader', avatar: '/images/company/team/56977038_2569784843034664_1072315757418774528_n@2x.png' },
      { name: 'Diego Niquefa', position: 'Senior Full-stack Developer', avatar: '/images/company/team/Niquefa@2x.png' },
      { name: 'Miguel Cortes', position: 'Full-stack Developer', avatar: '/images/company/team/pp@sd2x.png' },
      { name: 'Miguel Cortes', position: 'Senior Full-stack Developer', avatar: '/images/company/team/IMG_9660@2x.png' }
    ]
  }),
  computed: {
    chunkedItems() {
      const items = this.items.slice()
      return [].concat.apply([], items.map((el, i) => i % 4 ? [] : [items.slice(i, i + 4)]))
    }
  }
}
</script>
