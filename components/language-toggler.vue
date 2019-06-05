<template>
  <v-menu
    offset-y
    :left="left"
    open-on-hover
    :content-class="contentClass"
    :nudge-width="100">
    <template v-slot:activator="{ on }">
      <slot name="label" :on="on" />
    </template>
    <v-list>
      <v-list-tile
        v-for="(row, index) in languages"
        :key="index">
        <div class="language-row" :class="{'language-active': activeLanguage === row.lang}">
          <span class="language-lang">{{ row.lang }}</span>
          <span class="language-name">{{ row.name }}</span>
        </div>
      </v-list-tile>
    </v-list>
  </v-menu>
</template>

<script>
export default {
  props: {
    left: Boolean,
    footerDropdown: Boolean
  },
  computed: {
    contentClass() {
      return 'language-toggler-dropdown' + (this.footerDropdown ? ' language-toggler-dropdown-footer' : '')
    }
  },
  data() {
    return {
      languages: [
        { name: 'Español', lang: 'es' },
        { name: 'English', lang: 'en' }
      ],
      activeLanguage: 'es'
    }
  }
}
</script>

<style lang="scss">
.language-toggler-dropdown {
  padding: 15px 35px !important;
  background: #f4f8fe !important;
  border-radius: 20px !important;
  box-shadow: 0 28px 30px rgba(145, 162, 184, 0.31) !important;
  .v-list {
    background: #f4f8fe !important;
  }
  &.language-toggler-dropdown-footer {
    @media (max-width: 600px) {
      left: calc(50% - 91px) !important;
    }
  }
}
.language-row {
  cursor: pointer;
  .language-lang {
    width: 30px;
    color: #fff;
    height: 30px;
    font-size: 13px;
    line-height: 30px;
    font-weight: bold;
    text-align: center;
    margin-right: 12px;
    border-radius: 9px;
    background: #91a2b8;
    display: inline-block;
    text-transform: uppercase;
  }
  .language-name {
    color: #91a2b8;
    font-weight: 700;
  }
  &.language-active {
    .language-lang {
      background: #354964;
    }
    .language-name {
      color: #354964;
    }
  }
  &:hover {
    .language-lang {
      background: #354964;
    }
    .language-name {
      color: #354964;
    }
  }
}
</style>
