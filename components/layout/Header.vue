<template lang="pug">
  header.header-page
    .wrapper_inner
      <MobileNav />
      nuxt-link(to="/").logo
        span.logo--icon(v-html="logoIcon")
        strong.logo--caption CoinLoan
      <UserNav />
</template>

<script>
import UserNav from '~/components/header/UserNav.vue'
import MobileNav from '~/components/header/MobileNav.vue'
export default {
  components: {
    UserNav,
    MobileNav,
  },
  data() {
    return {
      logoIcon: `<svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 32 32"><g transform="translate(-223 -18)"><path fill="#fff" d="M239.17 39.27a5.42 5.42 0 0 1-.25-10.82h.14l.06-.01h.05a5.42 5.42 0 0 1 0 10.83zm7.64-11.17a1.12 1.12 0 0 0-.8-1.91c-.3 0-.58.12-.8.33l-1.3 1.32a7.59 7.59 0 0 0-3.83-1.6v-2.12a1.12 1.12 0 0 0-2.25 0v2.19c-1.16.2-2.27.68-3.22 1.39l-1.65-1.6c-.2-.21-.49-.33-.78-.33h-.01a1.12 1.12 0 0 0-.77 1.93l1.62 1.59c-.69.92-1.16 2-1.38 3.12h-2.52a1.12 1.12 0 0 0 0 2.25h2.43c.12 1.12.49 2.2 1.07 3.17l-1.8 1.82a1.12 1.12 0 0 0 1.6 1.58l1.65-1.67a7.6 7.6 0 0 0 3.76 1.83v1.99a1.12 1.12 0 0 0 2.25 0v-1.92a7.58 7.58 0 0 0 3.96-1.7l1.47 1.43a1.12 1.12 0 0 0 1.59-.02c.43-.44.42-1.15-.02-1.58l-1.53-1.5a7.63 7.63 0 0 0 1.23-3.43h2.14a1.12 1.12 0 0 0 0-2.25h-2.23a7.67 7.67 0 0 0-1.24-2.94z"/><path fill="#fff" d="M238.9 47.56a13.67 13.67 0 0 1-13.65-13.65c0-7.54 6.12-13.66 13.66-13.66 7.53 0 13.65 6.12 13.65 13.66 0 7.53-6.12 13.65-13.65 13.65zM223 33.91c0 8.77 7.14 15.9 15.9 15.9 8.78 0 15.91-7.13 15.91-15.9S247.68 18 238.91 18 223 25.14 223 33.9z"/></g></svg>`,
    }
  },
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .wrapper_inner {
    max-width: 100%;
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .header-page {
    background-color: $clr-primary;
    color: $clr-secondary;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    padding: 16px 33px;
    box-shadow: 0 2px 4px rgb(166 166 166 / 50%);

    @media screen and (max-width: 768px) {
      position: static;
    }
  }

  .logo {
    display: flex;
    align-items: center;
    color: $clr-secondary;

    &--icon {
      border: 1px solid $clr-secondary;
      border-radius: 4px;
      margin-right: 8px;
      width: 32px;
      height: 32px;
      padding: 4px;
    }

    &--caption {
      font-size: 2rem;
      letter-spacing: 0.03em;
      font-weight: 500;
    }

    @media screen and (max-width: 768px) {
      display: none;
    }
  }

</style>