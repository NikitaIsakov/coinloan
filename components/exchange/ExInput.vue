<template lang="pug">
  input.form--control(type="text" :placeholder="inputPlaceholder" @keydown="checkVal($event)" @blur="validValBlur" :value="this.inputVal")
</template>

<script>
export default {
  props: ['inputVal','inputPlaceholder'],
  data() {
    return {
      valuta: this.inputVal,
      regex: /[^\d\.]/,
    }
  },
  methods: {
    checkVal: function(evt) {
      this.valuta = evt.target.value;
      this.validVal(evt, evt.target.value);
      this.$emit('valutaVal', {
        value: this.valuta,
      })
    },
    validVal: function(evt) {
      const charCode = evt.which;
      console.log(evt);
      // if (this.regex.test(evt.key) && !(charCode >= 37 && charCode <= 40) && (charCode != 8) && (charCode != 46)) {
      //   console.log(true)
      //   evt.preventDefault();
      // }
    },
    validValBlur: function() {
      if (this.regex.test(this.valuta)) {
        this.valuta = '';
      }
    }
  }
}
</script>