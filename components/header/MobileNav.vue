<template lang="pug">
  .mobile--navigation(:class="{'is-active': isActive}")
    button.btn.btn__toggle(type="button" @click.preventDefault="toggleMobileNav")
      span.caption Меню
    .navigation
      .navigation--content
        ul.navigation--list
          li.navigation--item(v-for="(item, index) in navList" :key="index")
            nuxt-link.navigation--link(:to="item.slug")
              | {{item.caption}}
        <SelectLang />
</template>

<script>
import SelectLang from '@/components/aside/SelectLang.vue';

export default {
  components: {
    SelectLang,
  },
  data() {
    return {
      isActive: false,
      navList: [
        {
          slug: '#',
          caption: 'Мой кошелёк'
        },
        {
          slug: '#',
          caption: 'Накопительный счёт'
        },
        {
          slug: '#',
          caption: 'Мгновенный займ'
        },
        {
          slug: '#',
          caption: 'Мои кредиты'
        },
        {
          slug: '/',
          caption: 'Обмен криптовалюты'
        },
        {
          slug: '#',
          caption: 'Реферальная программа'
        },
        {
          slug: '#',
          caption: 'Поддержка'
        },
      ]
    }
  },
  methods: {
    toggleMobileNav: function() {
      this.isActive = !this.isActive;
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .navigation {
    position: absolute;
    left: 0;
    top: 0;
    width: 0%;
    height: 0%;
    background-color: $clr-primary;
    transition: all 0.2s ease;
    z-index: 9;
    padding-top: 100px;

    &--list {
      padding: 0;
      margin: 0;
      list-style: none;
      text-align: center;
      margin-bottom: 20px;
    }

    &--content {
      opacity: 0;
      transition: 0.2s opacity 0.2s ease;
    }

    &--item {
      &:not(:last-child) {
        margin-bottom: 15px;
      }
    }

    &--link {
      color: $clr-secondary;
      font-size: 1.8rem;
      transition: opacity 0.2s ease;

      &:hover,
      &:focus {
        opacity: 0.8;
      }
    }
  }

  .mobile--navigation {
    display: none;

    .btn__toggle {
      border: none;
      background-color: transparent;
      font: inherit;
      color: inherit;
      padding: 0;
      margin: 0;
      font-size: 0;
      line-height: 0;
      width: 20px;
      height: 15px;
      z-index: 10;

      .caption {
        display: block;
        background-color: $clr-secondary;
        width: 20px;
        height: 2px;
        border-radius: 4px;
        position: relative;
        z-index: 10;

        &::before,
        &::after {
          content: "";
          width: 100%;
          height: 100%;
          left: 0;
          position: absolute;
          background-color: currentColor;
          transition: transform 0.2s ease;
        }

        &::before {
          top: -300%;
        }

        &::after {
          top: 300%;
        }
      }
    }

    &.is-active {
      .navigation {
        width: 100%;
        height: 100%;

        &--content {
          opacity: 1;
        }
      }

      .btn__toggle {
        .caption {
          visibility: hidden;

          &::before,
          &::after {
            visibility: visible;
          }

          &::before {
            transform: translateY(6px) rotate(45deg);
          }

          &::after {
            transform: translateY(-6px) rotate(-45deg);
          }
        }
      }
    }

    @media screen and (max-width: 768px) {
      display: flex;
    }
  }

</style>