<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <hr>
    <!-- <button @click="result++">Click</button><br>
    {{ result }}
    <hr> -->
    <input v-model.number.lazy="arg1" type="number">
    <input v-model.number.lazy="arg2" type="number">
    = {{ result }}<br>
    <button @click="sum">+</button>
    <button @click="difference">-</button>
    <button @click="multiply">*</button>
    <button @click="division">/</button>
    <button @click="divisionFloor">/^</button>
    <button @click="pow">pow</button>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      arg1: 0,
      arg2: 0,
      result: 0,
    }
  },
  methods: {
    sum(){
      this.result = this.arg1 + this.arg2
    },
    difference(){
      this.result = this.arg1 - this.arg2
    },
    multiply(){
      this.result = this.arg1 * this.arg2
    },
    division(){
      // this.result = this.arg1 / this.arg2
      this.arg2 == 0 ? this.result = 'На ноль делить нельзя' : this.result = this.arg1 / this.arg2
    },
    divisionFloor(){
      this.arg2 == 0 ? this.result = 'На ноль делить нельзя' : this.result = Math.floor(this.arg1 / this.arg2)
    },
    pow(){
      this.result = Math.pow(this.arg1, this.arg2)
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
