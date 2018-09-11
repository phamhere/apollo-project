<template>
  <div class="container">

    <div class="content">
      <h1>Exchange</h1>
      <select name="" id="" v-model="selectedExchange">
        <option disabled value="">Please select one</option>
        <option :value="exchange" v-for="(exchange,i) in ccxt.exchanges" :key="i">{{exchange}}</option>
      </select>
      <p>Selected: {{ selectedExchange }}</p>
    </div>

    <div class="content">
      <h1>Pair</h1>
      <select name="" id="" v-model="selectedPair">
        <option value="">Please select one</option>
        <option value=""></option>
      </select>
      <p>Selected: {{ selectedPair }}</p>
      <p>Loading: {{ loadingMarkets() }}</p>
    </div>

    <div class="content">
      <h1>Trades</h1>
    </div>
  </div>
</template>

<script>
import Exchange from '../components/Exchange.vue'
import Pair from '../components/Pair.vue'
import Trades from '../components/Trades.vue'
let ccxt = require('ccxt')

export default {
  name: 'home',
  data () {
    return {
      ccxt: ccxt,
      selectedExchange: '',
      selectedPair: ''
    }
  },
  methods: {
    loadingMarkets () {
      (async () => {
        // eslint-disable-next-line
        let kraken = new ccxt.kraken()
        let markets = await kraken.load_markets()
        console.log(markets)
        return markets
      })()
    }
  },
  components: {
    'exchange': Exchange,
    'pair': Pair,
    'trades': Trades
  }
}
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.content {
  width: 300px;
  height: 450px;
  border: 1px solid black;
}
</style>
