<template>
  <div>
    <h1>{{msg}}</h1>
    <!-- <input type="text" id="myInput" @keyup="filterFunction ()" placeholder="Search for exchange...">
    <ul id="myUl">
      <li v-for="(exchange,i) in ccxt.exchanges" :key="i"><a href="#">{{exchange}}</a></li>
    </ul> -->
    <select name="" id="" v-model="selectedExchange">
      <option disabled value="">Please select one</option>
      <option :value="exchange" v-for="(exchange,i) in ccxt.exchanges" :key="i">{{exchange}}</option>
    </select>
    <p>Selected: {{ selectedExchange }}</p>
  </div>
</template>

<script>
export default {
  name: 'Exchange',
  props: ['ccxt', 'selectedExchange'],
  data () {
    return {
      msg: 'Exchange'
    }
  },
  methods: {
    filterFunction () {
      const input = document.getElementById('myInput')
      const filter = input.value.toUpperCase()
      const ul = document.getElementById('myUl')
      const li = ul.getElementsByTagName('li')

      for (let i = 0; i < li.length; i++) {
        let a = li[i].getElementsByTagName('a')[0]
        if (a.innerHTML.toUpperCase().indexOf(filter) > -1) {
          li[i].style.display = ''
        } else {
          li[i].style.display = 'none'
        }
      }
    }
  }
}
</script>

<style>
#myInput {
  width: 75%;
  font-size: 16px;
  padding: 12px 20px 12px 40px;
  border: 1px solid #ddd;
}
#myUl {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
#myUl li a {
  box-sizing: border-box;
  border: 1px solid #ddd;
  margin-top: -1px;
  background-color: #f6f6f6;
  padding: 12px;
  text-decoration: none;
  font-size: 16px;
  color: black;
  display: block;
  width: 75%;
  margin: 0 auto;
}
#myUl li a:hover:not(.header) {
  background-color: #eee;
}
</style>
