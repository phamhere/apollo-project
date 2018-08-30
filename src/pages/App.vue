<template>
  <div class="container">
    <exchange class="content"></exchange>
    <pair class="content"></pair>
    <trades class="content"></trades>
  </div>
</template>

<script>
import Exchange from '../components/Exchange.vue'
import Pair from '../components/Pair.vue'
import Trades from '../components/Trades.vue'
export default {
  name: 'home',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
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
}

.content {
  width: 300px;
  height: 450px;
  border: 1px solid black;
}
</style>
