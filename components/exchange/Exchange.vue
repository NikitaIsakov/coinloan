<template lang="pug">
  .wrap-cards
    <Card :title="'Обменять EUR на BTC'">
      form(slot="content")
        <ExchangeDesc v-show="tablet || mobile"/>
        <ExInput :inputSup="'Вы платите'" :inputSub="'Доступно:0 EUR'" :inputPlaceholder="'Сумма платежа'" />
        <ExInput :inputSup="'Вы получаете'" :inputSub="'Доступно:0 BTC'" :inputPlaceholder="'Сумма получения'"/>
        <ExchangeSubmit v-show="tablet || mobile"/>
    </Card>
    <Card :title="'Краткое описание'" v-show="desktop">
      form.wrap-description(slot="content")
        <ExchangeDesc />
        <ExchangeSubmit />
    </Card>
</template>

<script>
import Card from '@/components/exchange/Card';
import ExInput from '@/components/exchange/ExInput';
import ExchangeDesc from '@/components/exchange/ExchangeDesc';
import ExchangeSubmit from '@/components/exchange/ExchangeSubmit';

export default {
  components: {
    Card,
    ExInput,
    ExchangeDesc,
    ExchangeSubmit
  },
  data() {
    return {
      desktop: true,
      mobile: false,
      tablet: false,
      сurrencies: [],
      commissions: [],
      currencyList: [],
      exchangeRateList: [],
    }
  },
  mounted() {
    window.addEventListener('resize', this.updateWidth);
  },
  methods: {
    updateWidth() {
      if (document.documentElement.clientWidth <= 768) {
        this.mobile = true;
        this.desktop = false;
        this.tablet = false;
      } else if (document.documentElement.clientWidth > 768 && document.documentElement.clientWidth <= 1200) {
        this.mobile = false;
        this.desktop = false;
        this.tablet = true;
      } else {
        this.desktop = true;
        this.mobile = false;
        this.tablet = false;
      }
    },
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
      let curr = this.сurrencies;
      let min = 10;
      let max = 100;

      for (let i = 0; i < curr.length; i++) {
        for (let j = 0; j < curr.length; j++) {
          if (curr[i] != curr[j]) {
            this.exchangeRateList.push({pair: `${curr[i]}/${curr[j]}`, rate: Math.floor(Math.random() * (max - min + 1)) + min});
          }
        }
      }
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

</style>