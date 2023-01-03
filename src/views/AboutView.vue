<template>
  <div class="text-center">
    <v-col>
      <h1>Текущий курс биткоина</h1>
    </v-col>
    <section v-if="errored">
      <p>Упс.. Не удалось получить данные</p>
    </section>
    <section v-else>
      <div v-if="loading">Получение данных...</div>
      <div v-else>
        <v-col v-for="currency in info" :key="currency.description">
          <span class="font-weight-bold">
            {{ currency.description + ':'  }}
          </span>
          <span class="font-weight-normal">
            <span v-html="currency.symbol"></span>{{ currency.rate_float | currencydecimal }}
          </span>
        </v-col>
      </div>
    </section>
    <v-btn depressed @click="updateCurse">
      Обновить курс
    </v-btn>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data: () => ({
    info: null,
    loading: true,
    errored: false
  }),
  filters: {
    currencydecimal(value) {
      return value.toFixed(2);
    }
  },
  methods: {
    updateCurse() {
      this.loading = true;
      this.errored = false;
      axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi))
      .catch(error => 
      { 
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
    }
  },
  mounted() {
    axios
      .get('https://api.coindesk.com/v1/bpi/currentprice.json')
      .then(response => (this.info = response.data.bpi))
      .catch(error => 
      { 
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
}
};
</script>