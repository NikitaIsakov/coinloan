<template lang="pug">
  footer.aside--footer
    .footer--head
      h3.footer--title Контакты
      a(href="mailto:support@coinloan.io") support@coinloan.io
    ul.site--navigation
      li.site--item(v-for="(item, index) in navList" :key="index")
        nuxt-link.site--link(:to="item.slug")
          | {{item.caption}}
    .footer--outro
      p.copyright CoinLoan OÜ <br> Kaupmehe tn 7-9, Tallinn, 10114, Estonia
      p.copyright © 2022 CoinLoan
</template>

<script>
export default {
  data() {
    return {
      navList: [
        {
          slug: '#',
          caption: 'Вопросы и ответы'
        },
        {
          slug: '#',
          caption: 'Тарифы'
        },
        {
          slug: '#',
          caption: 'Политика конфиденциальности'
        },
        {
          slug: '#',
          caption: 'Условия использования'
        },
        {
          slug: '#',
          caption: 'Регламент GDPR'
        },
        {
          slug: '#',
          caption: 'Политика AML'
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .aside--footer {
    padding: 24px;
    position: relative;

    &::before {
      content: "";
      position: absolute;
      width: calc(100% - 48px);
      left: 20px;
      top: 0;
      height: 1px;
      background-color: $clr-decor;
    }

    .footer {
      &--head {
        margin-bottom: 30px;

        a {
          font-size: 1.2rem;
          color: $clr-text_primary;
        }
      }

      &--title {
        font-weight: 500;
        font-size: 1.4rem;
        margin: 0 0 0.25em;
      }

      &--outro {
        .copyright {
          font-size: 1rem;
          color: $clr-text_gray;
        }
      }
    }
  }

  .site {
    &--navigation {
      list-style: none;
      margin: 0;
      padding: 0;
    }

    &--item {
      &:not(:last-child) {
        margin-bottom: 5px;
      }
    }

    &--link {
      font-size: 1.2rem;
      color: $clr-text;
      transition: color 0.2s ease;

      &:hover,
      &:focus {
        color: $clr-text_primary;
      }
    }
  }

</style>