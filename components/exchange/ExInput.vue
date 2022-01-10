<template lang="pug">
  input.form--control(type="text" :placeholder="inputPlaceholder" @keydown="validVal" @input="checkVal($event)" @blur="validValBlur($event)" :value="valuta")
</template>

<script>
export default {
  props: ['inputVal','inputPlaceholder'],
  data() {
    return {
      valuta: this.inputVal,
      regex: /[^\d\.]/,
      fullRegex: /^\d+(\.\d+)?$/,
    }
  },
  methods: {
    emitVal() {
      this.$emit('valutaVal', {
        value: this.valuta,
      })
    },
    checkVal: function(evt) {
      this.valuta = evt.target.value;
      this.emitVal();
    },
    validVal: function(evt) {
      const charCode = evt.which;
      if (this.regex.test(evt.key) && !(charCode >= 37 && charCode <= 40) && (charCode != 8) && (charCode != 46)) {
        evt.preventDefault();
      }
    },
    validValBlur: function(evt) {
      if (this.fullRegex.test(this.valuta)) {
        this.valuta = Math.round((String(this.valuta)).replace(/^0+/, '') * 100) / 100;
      } else {
        this.valuta = '';
      }
    }
  },
  watch: { // надо убрать
    'inputVal': function(value) {
      this.valuta = value;
    }
  }
}
</script>