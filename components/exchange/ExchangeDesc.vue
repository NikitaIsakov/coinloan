<template lang="pug">
  ul.description--list
    li.description--item(v-if="full")
      .description--caption Ваш Евро баланс
      .description--value 0 EUR
    li.description--item
      .description--caption Ваш Евро баланс
      .description--value 0 EUR
    li.description--item
      .description--caption Ваш Евро баланс
      .description--value 0 EUR
</template>

<script>
export default {
  props: {
    full: {
      type: Boolean,
      default: true
    },
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
        margin-bottom: 10px;
      }
    }

    &--value {
      font-weight: 500;
    }
  }

</style>