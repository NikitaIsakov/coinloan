<template lang="pug">
  aside.page--aside
    <WalletNav />
    <SelectLang />
    <FooterNav />
</template>

<script>
import WalletNav from '@/components/aside/WalletNav.vue'
import SelectLang from '@/components/aside/SelectLang.vue'
import FooterNav from '@/components/aside/FooterNav.vue'
export default {
  components: {
    WalletNav, SelectLang, FooterNav,
  }
}
</script>

<style lang="scss" scoped>
  .page--aside {
    padding-top: 30px;
    box-shadow: 0 2px 4px rgb(220 220 220 / 50%);
    display: flex;
    flex-direction: column;
    justify-content: space-between;

    @media screen and (max-width: 768px) {
      display: none;
    }
  }

</style>