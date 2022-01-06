<template lang="pug">
  .wrap-select-lang
    .select-lang
      <v-select v-model="selected" :searchable="false" :reduce="(option) => option.code" :options="langList" :clearable="false"></v-select>
</template>

<script>
import vSelect from 'vue-select';

export default {
  components: {
    vSelect,
  },
  data() {
    return {
      selected: 'Ru',
      langList: [
        {
          label: 'Русский',
          code: 'Ru'
        },
        {
          label: 'English',
          code: 'En'
        },
        {
          label: 'Deutsch',
          code: 'De'
        },
      ]
    }
  },
}
</script>

<style lang="scss" scoped>
  @import '@/assets/scss/vars.scss';

  .wrap-select-lang {
    padding: 0 24px;
  }

</style>