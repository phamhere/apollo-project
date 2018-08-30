<template>
  <h1>{{msg}}</h1>
</template>

<script>
let ccxt = require('ccxt')
console.log(ccxt.exchanges)
export default {
  name: 'Exchange',
  data () {
    return {
      msg: 'Exchange'
    }
  }
}
</script>
