<template>
  <div class="text-center">
    <v-col>
      <h1>Курс биткоина</h1>
    </v-col>
    <v-col v-for="currency in info" :key="currency.description">
      <span class="font-weight-bold">
        {{ currency.description + ':'  }}
      </span>
      <span class="font-weight-normal">
        <span v-html="currency.symbol"></span>{{ currency.rate_float | currencydecimal }}
      </span>
    </v-col>
    <v-btn depressed @click="updateCurse">
      Обновить курс
    </v-btn>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: () => ({
    info: null
  }),
  filters: {
    currencydecimal(value) {
      return value.toFixed(2);
    }
  },
  methods: {
    updateCurse() {
      axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi));
    }
  },
  mounted() {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi));
}
};
</script>