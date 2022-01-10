<template lang="pug">
  .modal
    .modal--backdrop
      .modal--content
        .modal--header
          h2.modal--title Успех!
          button.btn.btn__close(@click="close") Закрыть
        .modal--body
</template>

<script>
export default {
  methods: {
    close() {
      this.$emit('close');
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .modal {
    &--backdrop {
      position: fixed;
      width: 100%;
      height: 100%;
      left: 0;
      top: 0;
      background-color: rgba(0, 0, 0, 0.3);
      display: flex;
      justify-content: center;
      align-items: center;
    }

    &--content {
      background-color: $clr-secondary;
      padding: 20px 40px;
      border-radius: 4px;
      position: relative;
    }

    &--title {
      font-size: 3.4rem;
    }

    &--header {
      display: flex;
    }

    .btn__close {
      padding: 0;
      margin: 0;
      width: 20px;
      height: 20px;
      position: absolute;
      right: 15px;
      top: 15px;
      font-size: 0;
      background-color: transparent;

      &::before,
      &::after {
        content: "";
        position: absolute;
        right: 0;
        top: 10px;
        width: 20px;
        height: 2px;
        background-color: $clr-primary;
        transform: rotate(45deg);
      }

      &::after {
        transform: rotate(-45deg);
      }
    }
  }

</style>