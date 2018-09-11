<template>
  <div>
    <h1>{{msg}}</h1>
    <select name="" id="" v-model="selectedPair">
      <option value="">Please select one</option>
      <option value=""></option>
    </select>
    <p>Selected: {{ selectedPair }}</p>
  </div>
</template>

<script>
export default {
  name: 'Pair',
  props: ['ccxt', 'selectedExchange', 'selectedPair', 'markets'],
  data () {
    return {
      msg: 'Pair'
    }
  }
}
</script>
