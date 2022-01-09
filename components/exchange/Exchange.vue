<template lang="pug">
  .wrap-cards
    <Card :title="`Обменять ${currentFirst} на ${currentSecond}`" :theme="'exchange'">
      form(slot="content")
        <ExchangeDesc :full="false"/>
        <ExFormControl :currencyList="сurrencies" :currencySelected="currentFirst" :inputSup="'Вы платите'" :inputSub="'Доступно:0 EUR'" :inputVal="valuteFirstVal" :inputPlaceholder="'Сумма платежа'" @valutaVal="valutaFirst" @currencyVal="currencyFirst"/>
        <ExFormControl :currencyList="сurrenciesSecond" :currencySelected="currentSecond" :inputSup="'Вы получаете'" :inputSub="'Доступно:0 BTC'" :inputVal="valuteSecondVal" :inputPlaceholder="'Сумма получения'" @valutaVal="valutaSecond" @currencyVal="currencySecond"/>
        <ExchangeSubmit/>
    </Card>
    <Card :title="'Краткое описание'" :theme="'exchange-description'">
      form.wrap-description(slot="content")
        <ExchangeDesc />
        <ExchangeSubmit />
    </Card>
</template>

<script>
import Card from '@/components/exchange/Card';
import ExFormControl from '@/components/exchange/ExFormControl';
import ExchangeDesc from '@/components/exchange/ExchangeDesc';
import ExchangeSubmit from '@/components/exchange/ExchangeSubmit';

export default {
  components: {
    Card,
    ExFormControl,
    ExchangeDesc,
    ExchangeSubmit
  },
  data() {
    return {
      valuteFirstVal: '',
      valuteSecondVal: '',
      currentFirst: 'RUB',
      currentSecond: 'EUR',
      currentRait: '',
      currentCommissions: '',
      сurrencies: [],
      commissions: [],
      currencyList: [],
      сurrenciesSecond: [],
      exchangeRateList: [],
    }
  },
  mounted() {
    this.updateCurrentVal();
    this.correctionCurriencyList();
  },
  methods: {
    generateCurList: function() {
      // Генерация валютных пар
      let curr = this.сurrencies;
      for (let i = 0; i < curr.length; i++) {
        for (let j = 0; j < curr.length; j++) {
          if (curr[i] != curr[j]) {
            this.currencyList.push({base_currency: curr[i], quote_currency: curr[j], commissifeon: this.commissions[Math.floor(Math.random() * (5))]});
          }
        }
      }
    },
    generateExRate: function() {
      // Генерация курса валют.
      const curr = this.сurrencies;
      const min = 10;
      const max = 100;

      for (let i = 0; i < curr.length; i++) {
        for (let j = 0; j < curr.length; j++) {
          if (curr[i] != curr[j]) {
            this.exchangeRateList.push({pair: `${curr[i]}/${curr[j]}`, rate: Math.floor(Math.random() * (max - min + 1)) + min});
          }
        }
      }
    },
    updateCurrentVal: function () {
      const currFirst = this.currentFirst;
      const currSecond = this.currentSecond;

      const currRaitItem = this.exchangeRateList.filter(function(item) {
        return item.pair === `${currFirst}/${currSecond}`;
      });
      const currItem = this.currencyList.filter(function(item) {
        return item.base_currency === currFirst && item.quote_currency === currSecond;
      })
      console.log(currRaitItem);
      this.currentRait = currRaitItem[0].rate;
      this.currentCommissions = currItem[0].commissifeon;
    },
    valutaFirst: function(data) {
      this.valuteFirstVal = data.value;
      this.valuteSecondVal = this.valutaTranslation(data.value);
    },
    valutaSecond: function(data) {
      this.valuteSecondVal = data.value;
      this.valuteFirstVal = this.valutaTranslation(data.value);
    },
    currencyFirst: function (data) {
      this.currentFirst = data;
      this.updateCurrentVal();
      this.correctionCurriencyList();
      this.valuteSecondVal = this.valutaTranslation(this.valuteFirstVal);
    },
    currencySecond: function(data) {
      this.currentSecond = data
      this.updateCurrentVal();
      this.correctionCurriencyList();
      this.valuteFirstVal = this.valutaTranslation(this.valuteSecondVal);
    },
    valutaTranslation: function(val) {
      return val * this.currentRait;
    },
    valutaReverse: function() {
      
    },
    correctionCurriencyList: function() {
      const currFirst = this.currentFirst;
      this.сurrenciesSecond = this.сurrencies.filter(function(f) { return f !== currFirst })
    }
  },
  async fetch() {
    this.сurrencies = await fetch(process.env.baseUrl + 'currencies').then(res => res.json());
    this.commissions = await fetch(process.env.baseUrl + 'commissions').then(res => res.json());
    this.generateCurList();
    this.generateExRate();
  },
}
</script>

<style lang="scss" scoped>
  .wrap-cards {
    display: flex;
  }

  .card {
    &__exchange {
      .description--list {
        @media screen and (min-width: 1201px) {
          display: none;
        }
      }

      .btn__submit {
        @media screen and (min-width: 1201px) {
          display: none;
        }
      }
    }
  }

</style>