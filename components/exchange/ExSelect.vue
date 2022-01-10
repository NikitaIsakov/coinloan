<template lang="pug">
  .form-control--select
    <v-select v-model="value" :options="selectList" :clearable="false"  @input="setSelected"></v-select>
</template>

<script>
import vSelect from 'vue-select';

export default {
  props: ['selectList', 'selectedVal'],
  components: {
    vSelect,
  },
  data() {
    return {
      value: this.selectedVal,
    }
  },
  methods: {
    setSelected: function(val) {
      this.$emit("input", val);
    }
  }
}
</script>