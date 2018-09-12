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
        <option :value="key" v-for="(value,key,i) in markets" :key="i">{{ key }}</option>
      </select>
      <p>Selected: {{ selectedPair }}</p>
      <span>{{ loadingMarkets() }}</span>
    </div>

    <div class="content trades">
      <h1>Trades</h1>
      <table>
        <tr>
          <td>Size</td>
          <td>Price ( USD )</td>
          <td>Time</td>
        </tr>
        <tr v-for="(trade,i) in tradeData" :key="i">
          <td>{{ trade.amount }}</td>
          <td>{{ trade.price }}</td>
          <td>{{ trade.datetime }}</td>
        </tr>
      </table>
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
      selectedPair: '',
      markets: '',
      tradeData: []
    }
  },
  methods: {
    loadingMarkets () {
      (async () => {
        // eslint-disable-next-line
        let exchange = new ccxt[this.selectedExchange]()
        let markets = await exchange.load_markets()
        this.markets = markets
        this.tradeData = await exchange.fetchTrades(this.selectedPair)
      })()
    }
  },
  components: {
    exchange: Exchange,
    pair: Pair,
    trades: Trades
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
.trades table {
  margin: 0 auto;
  font-size: 10px;
}
</style>
