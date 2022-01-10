<template lang="pug">
  ul.description--list
    li.description--item(v-if="full")
      .description--caption {{exDesc.baseCurrency.caption}}
      .description--value {{exDesc.baseCurrency.value}}
    li.description--item(v-if="full")
      .description--caption {{exDesc.quoteCurrency.caption}}
      .description--value {{exDesc.quoteCurrency.value}}
    li.description--item
      .description--caption {{exDesc.rateCaption.caption}}
      .description--value {{exDesc.rateCaption.value}}
</template>

<script>
export default {
  props: {
    full: {
      type: Boolean,
      default: true
    },
    exDesc: {
      type: Object,
    }
  }
}
</script>

<style lang="scss" scoped>
  .description {
    &--list {
      padding: 0;
      margin: 0;
      list-style: none;
      margin-bottom: 20px;
    }

    &--item {
      display: flex;
      align-items: center;
      justify-content: space-between;

      &:not(:last-child) {
        margin-bottom: 15px;
      }
    }

    &--value {
      font-weight: 500;
    }
  }

</style>