<template lang="pug">
  section.page--content
    .content--header
      .content--icon(v-html="headIcon")
      h1.page--title Обмен криптовалюты
    <Exchange />
</template>

<script>
import Exchange from '@/components/exchange/Exchange'

export default {
  components: {
    Exchange,
  },
  data() {
    return {
      headIcon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="exchange" role="img" xmlns="http://www.w3.org/2000/svg" width="24" viewBox="0 0 512 512" class="wallet-nav__icon svg-inline--fa fa-exchange fa-w-16"><g class="fa-group"><path fill="#c6c6c6" d="M488 384H106l30.47 27.73a24 24 0 0 1 .47 34.4L126.13 457a24 24 0 0 1-33.94 0L9.37 374.63a32 32 0 0 1 0-45.26L92.19 247a24 24 0 0 1 33.94 0L137 257.87a24 24 0 0 1-.47 34.4L106 320h382a24 24 0 0 1 24 24v16a24 24 0 0 1-24 24z" class="fa-secondary"></path><path fill="#000" d="M0 168v-16a24 24 0 0 1 24-24h382l-30.5-27.73a24 24 0 0 1-.47-34.4L385.87 55a24 24 0 0 1 33.94 0l82.82 82.34a32 32 0 0 1 0 45.26L419.81 265a24 24 0 0 1-33.94 0L375 254.13a24 24 0 0 1 .47-34.4L406 192H24a24 24 0 0 1-24-24z" class="fa-primary"></path></g></svg>`
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .page--content {
    background-color: $clr-bg-content;
    padding: 50px 35px 25px;

    @media screen and (max-width: 768px) {
      padding: 25px 15px;
    }
  }

  .page--title {
    font-size: 2.4rem;
    font-weight: 500;
    margin: 0;
  }

  .content--header {
    display: flex;
    align-items: center;
    margin-bottom: 25px;

    @media screen and (max-width: 1200px) {
      display: none;
    }
  }

  .content--icon {
    margin-right: 15px;
    display: flex;
  }
</style>