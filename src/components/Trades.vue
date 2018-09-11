<template>
  <h1>{{msg}}</h1>
</template>

<script>
export default {
  name: 'Trades',
  props: ['ccxt'],
  data () {
    return {
      msg: 'Trades'
    }
  }
}
</script>
