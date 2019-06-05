<template>
  <v-container class="text-xs-center main-container" :class="{'tellers-page': isTellersPage}">
    <div class="mb-4">
      <h2 class="top-title mb-1">
        ¿No estás en Colombia o Ecuador?
      </h2>
      <p class="sub-title">
        deja tu correo y te notificaremos cuando estemos en tu país
      </p>
    </div>
    <span class="action-container rounded-8">
      <input type="email" name="" placeholder="Email" class="py-1 px-2">
      <v-btn depressed color="primary" class="mr-0 my-0 text-capitalize rounded-8">
        Suscribirme
      </v-btn>
    </span>
  </v-container>
</template>

<script>
export default {
  props: {
    isTellersPage: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
.main-container {
  padding: 4rem 0;
  background: #f2fafd;
  border-radius: 40px;
  .sub-title {
    font-size: 0.95rem;
    letter-spacing: -0.5px;
  }
  .action-container {
    background: #fff;
    padding-left: 0.7rem;
    display: inline-block;
    input:focus {
      outline: none;
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
  }
  &.tellers-page {
    background: #f0fdf5;
    .top-title {
      color: #0e7e7b;
    }
    .sub-title {
      color: #007774;
    }
    button {
      background: #007774 !important;
    }
  }
}
</style>
