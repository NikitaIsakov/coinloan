<template lang="pug">
  ul.wallet--navigation
    li.wallet--item(v-for="(item, index) in navList" :key="index")
      nuxt-link.wallet--link(:to="item.slug")
        span.item--icon(v-html="item.icon")
        span.item--caption
          | {{item.caption}}
</template>

<script>
export default {
  data() {
    return {
      navList: [
        {
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="wallet" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" class="wallet-nav__icon svg-inline--fa fa-wallet fa-w-16"><g class="fa-group"><path fill="currentColor" d="M416 272a32 32 0 1 0 32 32 32 32 0 0 0-32-32zm16-240H64A64 64 0 0 0 0 96a32 32 0 0 0 32 32h48a16 16 0 0 1 0-32h384a16 16 0 0 0 16-16 48 48 0 0 0-48-48z" class="fa-secondary"></path><path fill="currentColor" d="M461.2 128H32A32 32 0 0 1 0 96v320a64 64 0 0 0 64 64h397.2c28 0 50.8-21.53 50.8-48V176c0-26.47-22.78-48-50.8-48zM416 336a32 32 0 1 1 32-32 32 32 0 0 1-32 32z" class="fa-primary"></path></g></svg>`,
          caption: 'Мой кошелёк',
          slug: '#1',
        },
        {
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="percent" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512" class="wallet-nav__icon svg-inline--fa fa-percent fa-w-14"><g class="fa-group"><path fill="currentColor" d="M336 288a112 112 0 1 0 112 112 111.94 111.94 0 0 0-112-112zm0 160a48 48 0 1 1 48-48 48 48 0 0 1-48 48zM112 0a112 112 0 1 0 112 112A111.94 111.94 0 0 0 112 0zm0 160a48 48 0 1 1 48-48 48 48 0 0 1-48 48z" class="fa-secondary"></path><path fill="currentColor" d="M4.7 474.1l368-463.7A24 24 0 0 1 392.3.2l31.6-.1c19.4-.1 30.9 21.8 19.7 37.8L77.4 501.6a24 24 0 0 1-19.6 10.2l-33.4.1c-19.5 0-30.9-21.9-19.7-37.8z" class="fa-primary"></path></g></svg>`,
          caption: 'Накопительный счёт',
          slug: '#2',
        },
        {
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="money-check-edit-alt" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512" class="wallet-nav__icon svg-inline--fa fa-money-check-edit-alt fa-w-20"><g class="fa-group"><path fill="currentColor" d="M608 160H437l120.27 120.25A64 64 0 0 1 576 325.51V400a16 16 0 0 1-16 16H264a8 8 0 0 1-8-8v-16a8 8 0 0 1 8-8h163l-64-64h-99a8 8 0 0 1-8-8v-16a8 8 0 0 1 8-8h67L203 160H32a32 32 0 0 0-32 32v288a32 32 0 0 0 32 32h576a32 32 0 0 0 32-32V192a32 32 0 0 0-32-32zM144 415.85V432a8 8 0 0 1-8 8h-16a8 8 0 0 1-8-8v-16.32a57.32 57.32 0 0 1-31.37-11.35 8 8 0 0 1-.57-12.14L91.81 381a8.19 8.19 0 0 1 10.13-.73 24.06 24.06 0 0 0 12.82 3.73h28.11c6.5 0 11.8-5.92 11.8-13.19 0-5.95-3.61-11.19-8.77-12.73l-45-13.5c-18.59-5.58-31.58-23.45-31.58-43.42 0-24.52 19.05-44.44 42.67-45.07V240a8 8 0 0 1 8-8h16a8 8 0 0 1 8 8v16.29a57.17 57.17 0 0 1 31.37 11.35 8 8 0 0 1 1.4 11.22 7.26 7.26 0 0 1-.83.92L164.18 291a8.22 8.22 0 0 1-10.13.73 24 24 0 0 0-12.82-3.73h-28.11c-6.5 0-11.8 5.92-11.8 13.19 0 5.95 3.61 11.19 8.77 12.73l45 13.5c18.59 5.58 31.58 23.42 31.58 43.39 0 24.5-19.05 44.41-42.67 45.04z" class="fa-secondary"></path><path fill="currentColor" d="M238.78 7a24.1 24.1 0 0 0-33.9 0L167 44.84a24 24 0 0 0 0 33.8l41.9 41.9 71.7-71.8zm295.86 295.88L303.18 71.44l-71.7 71.7 231.4 231.46a32 32 0 0 0 22.62 9.4H528a16 16 0 0 0 16-16v-42.49a32 32 0 0 0-9.36-22.63zm-379.55 24.51l-45-13.5c-5.16-1.54-8.77-6.78-8.77-12.73 0-7.27 5.3-13.19 11.8-13.19h28.11a24 24 0 0 1 12.82 3.73 8.22 8.22 0 0 0 10.13-.73l11.75-11.22a7.26 7.26 0 0 0 .83-.92 8 8 0 0 0-1.4-11.22A57.17 57.17 0 0 0 144 256.26V240a8 8 0 0 0-8-8h-16a8 8 0 0 0-8 8v16.12c-23.62.63-42.67 20.55-42.67 45.07 0 20 13 37.81 31.58 43.39l45 13.5c5.16 1.54 8.77 6.78 8.77 12.73 0 7.27-5.3 13.19-11.8 13.19h-28.12a24.06 24.06 0 0 1-12.82-3.73 8.19 8.19 0 0 0-10.13.73l-11.75 11.19a8 8 0 0 0 .57 12.14A57.32 57.32 0 0 0 112 415.68V432a8 8 0 0 0 8 8h16a8 8 0 0 0 8-8v-16.15c23.62-.63 42.67-20.54 42.67-45.07 0-19.97-12.99-37.78-31.58-43.39z" class="fa-primary"></path></g></svg>`,
          caption: 'Мгновенный займ',
          slug: '#3',
        },
        {
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="briefcase" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" class="wallet-nav__icon svg-inline--fa fa-briefcase fa-w-16"><g class="fa-group"><path fill="currentColor" d="M320 288h192v144c0 25.6-22.4 48-48 48H48c-25.6 0-48-22.4-48-48V288h192v48a16 16 0 0 0 16 16h96a16 16 0 0 0 16-16z" class="fa-secondary"></path><path fill="currentColor" d="M464 128h-80V80c0-25.6-22.4-48-48-48H176c-25.6 0-48 22.4-48 48v48H48c-25.6 0-48 22.4-48 48v80h512v-80c0-25.6-22.4-48-48-48zm-144 0H192V96h128z" class="fa-primary"></path></g></svg>`,
          caption: 'Мои кредиты',
          slug: '#4',
        },
        {
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="exchange" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" class="wallet-nav__icon svg-inline--fa fa-exchange fa-w-16"><g class="fa-group"><path fill="currentColor" d="M488 384H106l30.47 27.73a24 24 0 0 1 .47 34.4L126.13 457a24 24 0 0 1-33.94 0L9.37 374.63a32 32 0 0 1 0-45.26L92.19 247a24 24 0 0 1 33.94 0L137 257.87a24 24 0 0 1-.47 34.4L106 320h382a24 24 0 0 1 24 24v16a24 24 0 0 1-24 24z" class="fa-secondary"></path><path fill="currentColor" d="M0 168v-16a24 24 0 0 1 24-24h382l-30.5-27.73a24 24 0 0 1-.47-34.4L385.87 55a24 24 0 0 1 33.94 0l82.82 82.34a32 32 0 0 1 0 45.26L419.81 265a24 24 0 0 1-33.94 0L375 254.13a24 24 0 0 1 .47-34.4L406 192H24a24 24 0 0 1-24-24z" class="fa-primary"></path></g></svg>`,
          caption: 'Обмен криптовалюты',
          slug: '/',
        },
        {
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="users" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 640 512" class="wallet-nav__icon svg-inline--fa fa-users fa-w-20"><g class="fa-group"><path fill="currentColor" d="M96 224a64 64 0 1 0-64-64 64.06 64.06 0 0 0 64 64zm480 32h-64a63.81 63.81 0 0 0-45.1 18.6A146.27 146.27 0 0 1 542 384h66a32 32 0 0 0 32-32v-32a64.06 64.06 0 0 0-64-64zm-512 0a64.06 64.06 0 0 0-64 64v32a32 32 0 0 0 32 32h65.9a146.64 146.64 0 0 1 75.2-109.4A63.81 63.81 0 0 0 128 256zm480-32a64 64 0 1 0-64-64 64.06 64.06 0 0 0 64 64z" class="fa-secondary"></path><path fill="currentColor" d="M396.8 288h-8.3a157.53 157.53 0 0 1-68.5 16c-24.6 0-47.6-6-68.5-16h-8.3A115.23 115.23 0 0 0 128 403.2V432a48 48 0 0 0 48 48h288a48 48 0 0 0 48-48v-28.8A115.23 115.23 0 0 0 396.8 288zM320 256a112 112 0 1 0-112-112 111.94 111.94 0 0 0 112 112z" class="fa-primary"></path></g></svg>`,
          caption: 'Реферальная программа',
          slug: '#6',
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .wallet {
    &--navigation {
      padding: 0;
      margin: 0;
      list-style: none;

      .item {
        &--icon {
          max-width: 30px;
          width: 100%;
          padding: 0 7px;
          margin-right: 15px;
        }

        &--caption {
          color: $clr-text;
          font-weight: 500;
          transition: color 0.2s ease;
        }
      }
    }

    &--item {
      padding: 0 20px 0 30px;
      position: relative;
      min-height: 41px;
      display: flex;
      align-items: center;

      &:not(:last-child) {
        margin-bottom: 20px;
      }
    }

    &--link {
      display: flex;
      align-items: center;
      width: 100%;

      &:hover,
      &:focus {
        .item--caption {
          color: $clr-text_primary;
        }
      }

      &.nuxt-link-exact-active {
        &::before {
          content: '';
          width: 3px;
          height: 100%;
          position: absolute;
          left: 0;
          top: 0;
          background-color: $clr-text_primary;
        }

        .item--caption {
          color: $clr-text_primary;
        }
      }
    }
  }

</style>