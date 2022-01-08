<template lang="pug">
  .card(:class="'card__' + theme")
    .card--header
      h2.card--title {{title}}
    .card--content
      <slot name="content"></slot>
</template>

<script>
export default {
  props: ['title', 'theme'],
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
      @media screen and (min-width: 1201px) {
        margin-right: 15px;
      }
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

    &__exchange {
      .description--list {
        display: none;

        @media screen and (max-width: 1200px) {
          display: block;
        }
      }

      .btn__submit {
        display: none;

        @media screen and (max-width: 1200px) {
          display: block;
        }
      }
    }

    &__exchange-description {
      @media screen and (max-width: 1200px) {
        display: none;
      }
    }

    @media screen and (max-width: 768px) {
      padding: 20px;
    }
  }

</style>