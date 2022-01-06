<template lang="pug">
  .card
    .card--header
      h2.card--title {{title}}
    .card--content
      <slot name="content"></slot>
</template>

<script>
export default {
  props: ['title'],
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .card {
    padding: 40px;
    background-color: $clr-secondary;
    border: 1px solid $clr-decor;
    border-radius: 5px;
    max-width: 420px;
    width: 100%;

    &:not(:last-child) {
      margin-right: 15px;
    }

    &--header {
      border-bottom: 1px solid $clr-decor;
    }

    &--title {
      margin: 0;
      margin-bottom: 1em;
    }

    &--content {
      padding: 25px 0;
      height: 100%;
    }
  }

</style>