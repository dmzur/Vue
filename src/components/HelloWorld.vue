<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <hr>
    <div class="errorDivi">
      {{err}}
    </div>
    <input id="input1" v-model.number.lazy="arg1" type="number">
    <input id="input2" v-model.number.lazy="arg2" type="number">
    = {{ result }}<br>
    <div class="keyboard">
      <button v-for="operand in operands" 
      :key="operand"
      :title="operand"
      @click="calculate(operand)">
      {{operand}}
      </button>
    </div>
    <hr>
    <div class="screenBoard">
      <input type="checkbox" id="keyB" v-model="showBoard">
      <label for="keyB">
        Включить экранную клавиатуру
        <hr>
        <div class="board" v-show="showBoard">
        <button v-for="number in numbers" :key="number" >{{number}}</button>
      </div>
      </label>
      
    </div>
    <hr>
    <div class="logs">
      История ввода
      <div v-for="(log, id) in logs" :key="id">{{log}}</div>
    </div>
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
      numbers: [1,2,3,4,5,6,7,8,9,0],
      operands: ['+','-','*','/','/int','pow'],
      boardInput:[],
      err: "",
      logs: {},
      showBoard: false,
    }
  },
  methods: {
    setboard(){
      this.boardInput.push()
    },
    
    calculate(operation = "+"){
      this.err = "";
      switch(operation){
        case "+": 
          this.sum();
          break;
        case "-": 
          this.difference();
          break;
        case "*": 
          this.multiply();
          break;
        case "/": 
          this.division();
          break;
        case "/int": 
          this.divInt();
          break;
        case "pow": 
          this.pow();
          break;
      }
      const key = Date.now()
      const value = `${this.arg1}${operation}${this.arg2}=${this.result}`
      this.$set(this.logs, key, value)

    },
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
      if(this.arg2 === 0){
        this.result = "Ошибка!";
        this.err = "На ноль делить нельзя!"
      }else{
        this.result = this.arg1 / this.arg2
      }
      
    },
    divInt(){
      if(this.arg2 === 0){
        this.result = "Ошибка!";
        this.err = "На ноль делить нельзя!"
      }else{
      this.result = Math.floor(this.arg1 / this.arg2)
      }
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
