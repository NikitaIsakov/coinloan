<template lang="pug">
  .page-wrap
    <Header />
    main.main-page
      <Aside />
      <Main />
</template>

<script>
import Header from '@/components/layout/Header'
import Aside from '@/components/layout/Aside'
import Main from '@/components/layout/Main'

export default {
  components: {
    Header,
    Aside,
    Main,
  }
}
</script>

<style lang="scss" scoped>
  .main-page {
    min-height: calc(100vh - 64px);
  }

</style>