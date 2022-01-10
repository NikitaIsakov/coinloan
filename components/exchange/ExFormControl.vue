<template lang="pug">
  .form--group
    .form--control-suptitle {{inputSup}}
    .form--control-wrap
      <ExInput :inputVal="inputVal" :inputPlaceholder="inputPlaceholder" @valutaVal="collectionDataInput"/>
      <ExSelect :selectList="currencyList" :selectedVal="currencySelected" @input="collectionDataSelect"/>
    .form--control-subtitle {{inputSub}}
</template>

<script>
import ExInput from '@/components/exchange/ExInput'
import ExSelect from '@/components/exchange/ExSelect'

export default {
  components: {ExInput, ExSelect},
  props: ['inputSup', 'inputSub', 'inputVal','inputPlaceholder', 'currencyList', 'currencySelected'],
  methods: {
    collectionDataInput(data) {
      this.$emit('valutaVal', data);
    },
    collectionDataSelect(data) {
      this.$emit('currencyVal', data);
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .form {
    &--group {
      margin-bottom: 20px;
    }

    &--control {
      margin-bottom: 10px;
      width: 100%;
      border: 1px solid $clr-decor;
      padding: 12px 110px 12px 15px;
      outline: none;
      border-radius: 4px;
      transition: border-color 0.2s ease;

      &:hover,
      &:focus {
        border-color: $clr-primary;
      }

      &::placeholder {
        color: $clr-text_gray;
      }

      &-suptitle {
        font-weight: 500;
        font-size: 1.4rem;
        margin-bottom: 5px;
      }

      &-subtitle {
        font-size: 1.2rem;
        color: $clr-text_gray;
      }

      &-wrap {
        position: relative;
      }
    }
  }

</style>