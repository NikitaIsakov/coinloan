<template lang="pug">
  .user--navigation(v-bind:class="{ 'is-active': isActive }" ref="dropdown")
    button.navigation--toggle(type="button" @click.preventDefault="userNavToggle")
      span.navigation--icon(v-html="navIcon")
      span.navigation--caption Мой аккаунт
    ul.navigation--list(v-show="isActive")
      li.navigation--item(v-for="(item, index) in navList" :key="index")
        nuxt-link.item--link(:to="item.slug")
          span.item--icon(v-html="item.icon")
          span.item--caption
            | {{ item.text }}

</template>

<script>
export default {
  data() {
    return {
      isActive: false,
      navList: [
        {
          slug: '/',
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="far" data-icon="cog" role="img" xmlns="http://www.w3.org/2000/svg" width="13.14" height="13.56" viewBox="0 0 512 512" class="navigation-item__icon svg-inline--fa fa-cog fa-w-16"><path fill="currentColor" d="M452.515 237l31.843-18.382c9.426-5.441 13.996-16.542 11.177-27.054-11.404-42.531-33.842-80.547-64.058-110.797-7.68-7.688-19.575-9.246-28.985-3.811l-31.785 18.358a196.276 196.276 0 0 0-32.899-19.02V39.541a24.016 24.016 0 0 0-17.842-23.206c-41.761-11.107-86.117-11.121-127.93-.001-10.519 2.798-17.844 12.321-17.844 23.206v36.753a196.276 196.276 0 0 0-32.899 19.02l-31.785-18.358c-9.41-5.435-21.305-3.877-28.985 3.811-30.216 30.25-52.654 68.265-64.058 110.797-2.819 10.512 1.751 21.613 11.177 27.054L59.485 237a197.715 197.715 0 0 0 0 37.999l-31.843 18.382c-9.426 5.441-13.996 16.542-11.177 27.054 11.404 42.531 33.842 80.547 64.058 110.797 7.68 7.688 19.575 9.246 28.985 3.811l31.785-18.358a196.202 196.202 0 0 0 32.899 19.019v36.753a24.016 24.016 0 0 0 17.842 23.206c41.761 11.107 86.117 11.122 127.93.001 10.519-2.798 17.844-12.321 17.844-23.206v-36.753a196.34 196.34 0 0 0 32.899-19.019l31.785 18.358c9.41 5.435 21.305 3.877 28.985-3.811 30.216-30.25 52.654-68.266 64.058-110.797 2.819-10.512-1.751-21.613-11.177-27.054L452.515 275c1.22-12.65 1.22-25.35 0-38zm-52.679 63.019l43.819 25.289a200.138 200.138 0 0 1-33.849 58.528l-43.829-25.309c-31.984 27.397-36.659 30.077-76.168 44.029v50.599a200.917 200.917 0 0 1-67.618 0v-50.599c-39.504-13.95-44.196-16.642-76.168-44.029l-43.829 25.309a200.15 200.15 0 0 1-33.849-58.528l43.819-25.289c-7.63-41.299-7.634-46.719 0-88.038l-43.819-25.289c7.85-21.229 19.31-41.049 33.849-58.529l43.829 25.309c31.984-27.397 36.66-30.078 76.168-44.029V58.845a200.917 200.917 0 0 1 67.618 0v50.599c39.504 13.95 44.196 16.642 76.168 44.029l43.829-25.309a200.143 200.143 0 0 1 33.849 58.529l-43.819 25.289c7.631 41.3 7.634 46.718 0 88.037zM256 160c-52.935 0-96 43.065-96 96s43.065 96 96 96 96-43.065 96-96-43.065-96-96-96zm0 144c-26.468 0-48-21.532-48-48 0-26.467 21.532-48 48-48s48 21.533 48 48c0 26.468-21.532 48-48 48z" class=""></path></svg>`,
          text: 'Настройки',
        },
        {
          slug: '/',
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="far" data-icon="file-chart-line" role="img" xmlns="http://www.w3.org/2000/svg" width="10.5" height="14" viewBox="0 0 384 512" class="navigation-item__icon svg-inline--fa fa-file-chart-line fa-w-12"><path fill="currentColor" d="M131.2 320h-22.4c-6.4 0-12.8 6.4-12.8 12.8v70.4c0 6.4 6.4 12.8 12.8 12.8h22.4c6.4 0 12.8-6.4 12.8-12.8v-70.4c0-6.4-6.4-12.8-12.8-12.8zm72-64h-22.4c-6.4 0-12.8 6.4-12.8 12.8v134.4c0 6.4 6.4 12.8 12.8 12.8h22.4c6.4 0 12.8-6.4 12.8-12.8V268.8c0-6.4-6.4-12.8-12.8-12.8zm49.6 160h22.4c6.4 0 12.8-6.4 12.8-12.8V300.8c0-6.4-6.4-12.8-12.8-12.8h-22.4c-6.4 0-12.8 6.4-12.8 12.8v102.4c0 6.4 6.4 12.8 12.8 12.8zM369.83 97.98L285.94 14.1c-9-9-21.2-14.1-33.89-14.1H47.99C21.5.1 0 21.6 0 48.09v415.92C0 490.5 21.5 512 47.99 512h287.94c26.5 0 48.07-21.5 48.07-47.99V131.97c0-12.69-5.17-24.99-14.17-33.99zM255.95 51.99l76.09 76.08h-76.09V51.99zM336 464.01H47.99V48.09h159.97v103.98c0 13.3 10.7 23.99 24 23.99H336v287.95z" class=""></path></svg>`,
          text: 'Отчеты',
        },
        {
          slug: '/',
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="far" data-icon="user-tie" role="img" xmlns="http://www.w3.org/2000/svg" width="12.25" height="14" viewBox="0 0 448 512" class="navigation-item__icon svg-inline--fa fa-user-tie fa-w-14"><path fill="currentColor" d="M224 288c79.5 0 144-64.5 144-144S303.5 0 224 0 80 64.5 80 144s64.5 144 144 144zm0-240c52.9 0 96 43.1 96 96s-43.1 96-96 96-96-43.1-96-96 43.1-96 96-96zm91.9 256.2l-56.5 154.5L240 376l32-56h-96l32 56-19.5 82.7L132 304.2C58.9 305.5 0 365 0 438.4V464c0 26.5 21.5 48 48 48h352c26.5 0 48-21.5 48-48v-25.6c0-73.4-58.9-132.9-132.1-134.2zM96 464H48v-25.6c0-35.4 21.9-66.2 53-79.4l38.4 105H96zm304 0h-91.3L347 359c31 13.2 53 44 53 79.4V464z" class=""></path></svg>`,
          text: 'Верификация',
        },
        {
          slug: '/',
          icon: `<svg aria-hidden="true" focusable="false" data-prefix="far" data-icon="sign-out" role="img" xmlns="http://www.w3.org/2000/svg" width="14" height="10.5" viewBox="0 0 512 512" class="navigation-item__icon svg-inline--fa fa-sign-out fa-w-16"><path fill="currentColor" d="M96 64h84c6.6 0 12 5.4 12 12v24c0 6.6-5.4 12-12 12H96c-26.5 0-48 21.5-48 48v192c0 26.5 21.5 48 48 48h84c6.6 0 12 5.4 12 12v24c0 6.6-5.4 12-12 12H96c-53 0-96-43-96-96V160c0-53 43-96 96-96zm231.1 19.5l-19.6 19.6c-4.8 4.8-4.7 12.5.2 17.1L420.8 230H172c-6.6 0-12 5.4-12 12v28c0 6.6 5.4 12 12 12h248.8L307.7 391.7c-4.8 4.7-4.9 12.4-.2 17.1l19.6 19.6c4.7 4.7 12.3 4.7 17 0l164.4-164c4.7-4.7 4.7-12.3 0-17l-164.4-164c-4.7-4.6-12.3-4.6-17 .1z" class=""></path></svg>`,
          text: 'Выйти',
        },
      ],
      navIcon: `<svg aria-hidden="true" focusable="false" data-prefix="fad" data-icon="user" role="img" xmlns="http://www.w3.org/2000/svg" width="14" height="16" viewBox="0 0 448 512" class="svg-inline--fa fa-user fa-w-14"><g class="fa-group"><path fill="#aacdfd" d="M352 128A128 128 0 1 1 224 0a128 128 0 0 1 128 128z" class="fa-secondary"></path><path fill="#3482fa" d="M313.6 288h-16.7a174.1 174.1 0 0 1-145.8 0h-16.7A134.43 134.43 0 0 0 0 422.4V464a48 48 0 0 0 48 48h352a48 48 0 0 0 48-48v-41.6A134.43 134.43 0 0 0 313.6 288z" class="fa-primary"></path></g></svg>`
    }
  },
  mounted(){
    document.addEventListener('click', this.outsideClick)
  },
  destroyed () {
    document.removeEventListener('click', this.outsideClick)
  },
  methods: {
    userNavToggle: function() {
      this.isActive = !this.isActive;
    },
    outsideClick: function(e) {
      let el = this.$refs.dropdown;
      let target = e.target;
      if (el !== target && !el.contains(target)){
        this.isActive = false
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .user--navigation {
    position: relative;

    .navigation {
      &--toggle {
        border: none;
        padding: 0 25px 0 0;
        margin: 0;
        color: inherit;
        font: inherit;
        background-color: transparent;
        display: flex;
        align-items: center;
        position: relative;
        cursor: pointer;

        &::after {
          content: '';
          width: 20px;
          height: 20px;
          position: absolute;
          top: 50%;
          margin-top: -10px;
          right: 0;
          transition: transform 0.2s ease;
          background-repeat: no-repeat;
          background-size: contain;
          background-position: center;
          background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 24 24'%3E%3Cpath fill='%23fff' d='M7.406 8.578l4.594 4.594 4.594-4.594 1.406 1.406-6 6-6-6z'%3E%3C/path%3E%3C/svg%3E");
        }
      }

      &--icon {
        display: inline-block;
        background-color: $clr-secondary;
        border-radius: 50%;
        overflow: hidden;
        margin-right: 15px;
        padding: 4px;
        width: 26px;
        height: 26px;

        .fa-secondary {
          fill: $clr-third;
        }

        .fa-primary {
          fill: $clr-primary;
        }
      }

      &--list {
        margin: 0;
        padding: 0;
        list-style: none;
        position: absolute;
        width: 110%;
        top: 140%;
        right: 0;
        background-color: $clr-secondary;
        color: $clr-text;
        border-radius: 2px;
        box-shadow: 0 2px 4px rgb(223 223 223 / 50%);
      }

      &--item {
        margin: 0;
        padding: 10px 15px;

        &:not(:last-child) {
          border-bottom: 1px solid $clr-decor;
        }

        .item {
          &--icon {
            display: flex;
            align-items: center;
            margin: -1px 8px 0 0;
          }

          &--caption {
            transition: color 0.2s ease;
          }

          &--link {
            display: flex;
            align-items: center;
            color: $clr-text;
            font-weight: 500;

            &:hover,
            &:focus {
              .item--caption {
                color: $clr-text_primary;
              }
            }
          }
        }
      }
    }

    &.is-active {
      .navigation--toggle {
        &::after {
          transform: rotate(180deg);
        }
      }
    }
  }

</style>