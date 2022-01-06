<template lang="pug">
  <div>
    <Header />
    main.main
      <Aside />
      section.content
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
