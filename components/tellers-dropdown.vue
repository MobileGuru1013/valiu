<template>
  <v-menu
    offset-y
    :left="left"
    open-on-hover
    content-class="teller-toggler-dropdown"
    :nudge-width="100">
    <template v-slot:activator="{ on }">
      <slot name="label" :on="on" />
    </template>
    <v-list>
      <v-list-tile
        v-for="(row, index) in tellers"
        :key="index">
        <router-link tag="div" :to="row.value" class="tellers-row" :class="{'teller-active': $route.path === row.value}">
          <span class="teller-name">{{ row.name }}</span>
        </router-link>
      </v-list-tile>
    </v-list>
  </v-menu>
</template>

<script>
export default {
  props: {
    left: Boolean
  },
  data() {
    return {
      tellers: [
        { name: 'Convertirse En Un Cajero', value: '/tellers' },
        { name: 'Iniciar Sesión', value: '/login' },
        { name: 'Registrarme', value: '/register' }
      ]
    }
  }
}
</script>

<style lang="scss">
.teller-toggler-dropdown {
  padding: 15px 35px;
  border-radius: 20px;
  background: #eefffe;
  box-shadow: 0 12px 28px 6px rgba(23, 197, 162, 0.15);
  .v-list {
    background: #eefffe;
  }
}
.tellers-row {
  cursor: pointer;
  .teller-lang {
    width: 30px;
    color: #fff;
    height: 30px;
    font-size: 13px;
    line-height: 30px;
    font-weight: bold;
    text-align: center;
    margin-right: 12px;
    border-radius: 9px;
    background: #b0efe4;
    display: inline-block;
    display: none;
    text-transform: uppercase;
  }
  .teller-name {
    color: #b0efe4;
    font-weight: 700;
  }
  &:hover {
    .teller-lang {
      color: #17c5a2;
    }
    .teller-name {
      color: #17c5a2;
    }
  }
  &.teller-active {
    .teller-lang {
      color: #17c5a2;
    }
    .teller-name {
      color: #17c5a2;
    }
  }
}
</style>
