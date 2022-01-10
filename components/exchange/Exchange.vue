<template lang="pug">
  .exchange(:class="{ 'is-load': exLoad }")
    .wrap-cards
      <Card :title="`Обменять ${currentFirst} на ${currentSecond}`" :theme="'exchange'">
        form(slot="content" @submit.prevent="formSubmit")
          <ExDesc :full="false" :exDesc="exchangeDescription"/>
          <ExFormControl :currencyList="сurrenciesFirst" :currencySelected="currentFirst" :inputSup="'Вы платите'" :inputSub="`Доступно:0 ${currentFirst}`" :inputVal="valuteFirstVal" :inputPlaceholder="'Сумма платежа'" @valutaVal="valutaFirst" @currencyVal="currencyFirst"/>
          <ExFormControl :currencyList="сurrenciesSecond" :currencySelected="currentSecond" :inputSup="'Вы получаете'" :inputSub="`Доступно:0 ${currentSecond}`" :inputVal="valuteSecondVal" :inputPlaceholder="'Сумма получения'" @valutaVal="valutaSecond" @currencyVal="currencySecond"/>
          <ExSubmit/>
      </Card>
      <Card :title="'Краткое описание'" :theme="'exchange-description'">
        form.wrap-description(slot="content" @submit.prevent="formSubmit")
          <ExDesc :exDesc="exchangeDescription"/>
          <ExSubmit/>
      </Card>
</template>

<script>
import Card from '@/components/exchange/Card';
import ExFormControl from '@/components/exchange/ExFormControl';
import ExDesc from '@/components/exchange/ExDesc';
import ExSubmit from '@/components/exchange/ExSubmit';

export default {
  components: {
    Card,
    ExFormControl,
    ExDesc,
    ExSubmit
  },
  data() {
    return {
      exLoad: false,
      valuteFirstVal: '',
      valuteSecondVal: '',
      currentFirst: 'RUB',
      currentSecond: 'EUR',
      currentRate: '',
      currentRateReverse: '',
      currentCommissions: '',
      сurrencies: [],
      commissions: [],
      currencyList: [],
      сurrenciesFirst: [],
      сurrenciesSecond: [],
      exchangeRateList: [],
      exchangeDescription: {
        baseCurrency: {
          caption: `Ваш RUB баланс`,
          value: `0 RUB`,
        },
        quoteCurrency: {
          caption: `Ваш EUR баланс`,
          value: `0 EUR`,
        },
        rateCaption: {
          caption: 'Курс',
          value: `1 RUB = 80 EUR`,
        },
      },
    }
  },
  mounted() {
    this.correctionCurriencyList();
    this.updateDescriptionVal();
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
      this.exchangeRateList = [];
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

      this.updateCurrentVal();
    },
    updateCurrentVal: function () {
      this.exLoad = true;
      const currFirst = this.currentFirst;
      const currSecond = this.currentSecond;

      const currRateItem = this.exchangeRateList.filter(function(item) {
        return item.pair === `${currFirst}/${currSecond}`;
      });
      const currItem = this.currencyList.filter(function(item) {
        return item.base_currency === currFirst && item.quote_currency === currSecond;
      })

      this.currentRate = currRateItem[0].rate;
      this.currentCommissions = currItem[0].commissifeon;
      this.currentRateReverse = Math.round((1 / currRateItem[0].rate) * 10000) / 10000;

      this.exLoad = false;

      this.updateDescriptionVal();
      this.valuteSecondVal = this.valutaTranslation(this.valuteFirstVal, this.currentRate);
      this.valuteFirstVal = this.valutaTranslation(this.valuteSecondVal, this.currentRateReverse, true);
    },
    valutaFirst: function(data) {
      this.valuteFirstVal = data.value;
      this.valuteSecondVal = this.valutaTranslation(data.value, this.currentRate);
    },
    valutaSecond: function(data) {
      this.valuteSecondVal = data.value;
      this.valuteFirstVal = this.valutaTranslation(data.value, this.currentRateReverse, true);
    },
    currencyFirst: function (data) {
      this.currentFirst = data;
      this.updateCurrentVal();
      this.correctionCurriencyList();
      this.updateDescriptionVal();
      this.valuteSecondVal = this.valutaTranslation(this.valuteFirstVal, this.currentRate);
    },
    currencySecond: function(data) {
      this.currentSecond = data
      this.updateCurrentVal();
      this.correctionCurriencyList();
      this.updateDescriptionVal();
      this.valuteFirstVal = this.valutaTranslation(this.valuteSecondVal, this.currentRateReverse, true);
    },
    valutaTranslation: function(val, rate, reverse) {
      let commission = this.currentCommissions;
      if (reverse) {
        commission = 0;
      }
      return (val > 0) ? (Math.round(((val * rate) - ((val * rate) * (commission / 100))) * 100000000) / 100000000) : ''; // Округлил результат вычислений до 8 знаков после запятой
    },
    correctionCurriencyList: function() {
      const currFirst = this.currentFirst;
      const currSecond = this.currentSecond;
      this.сurrenciesSecond = this.сurrencies.filter(function(f) { return f !== currFirst })
      this.сurrenciesFirst = this.сurrencies.filter(function(f) { return f !== currSecond })
    },
    updateDescriptionVal: function() {
      this.exchangeDescription.baseCurrency.caption = `Ваш ${this.currentFirst} баланс`;
      this.exchangeDescription.baseCurrency.value = `0 ${this.currentFirst}`;
      this.exchangeDescription.quoteCurrency.caption = `Ваш ${this.currentSecond} баланс`;
      this.exchangeDescription.quoteCurrency.value = `0 ${this.currentSecond}`;
      this.exchangeDescription.rateCaption.value = `1 ${this.currentFirst} = ${this.currentRate} ${this.currentSecond}`;
    },
    formSubmit: function() {
      this.$emit('submit');
    }
  },
  async fetch() {
    this.сurrencies = await fetch(process.env.baseUrl + 'currencies').then(res => res.json());
    this.commissions = await fetch(process.env.baseUrl + 'commissions').then(res => res.json());
    this.generateCurList();
    this.generateExRate();

    this.refreshExRate = setInterval(function(){
      this.generateExRate();
    }.bind(this), 30000);
  },
}
</script>

<style lang="scss" scoped>
  .exchange {
    transition: opacity 0.2s ease;

    &.is-load {
      opacity: 0.6;
      pointer-events: none;
    }
  }

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