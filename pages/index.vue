<template lang="pug">
  <div class="page-wrap">
    <Header />
    main.main-page
      <Aside />
      section.page--content
        | main content
  </div>
</template>

<script>
import Header from '@/components/layout/Header'
import Aside from '@/components/layout/Aside'

export default {
  components: {
    Header,
    Aside
  }
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .page--content {
    background-color: $clr-bg-content;
  }

  .main-page {
    min-height: calc(100vh - 64px);
  }

</style>