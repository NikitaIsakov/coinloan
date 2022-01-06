<template lang="pug">
  .form--group
    .form--control-suptitle {{inputSup}}
    input.form--control(type="text" :placeholder="inputPlaceholder")
    .form--control-subtitle {{inputSub}}
</template>

<script>
export default {
  props: ['inputSup', 'inputSub', 'inputPlaceholder']
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
      padding: 12px 15px;

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
    }
  }

</style>