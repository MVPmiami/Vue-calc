<template>
  <div class="calculator">
    <input type="text" class="input" v-model="result" placeholder="0">
    <button class="clear-button" v-on:click='reset'>Clear</button>
  <div class='interface'>
    <div class="main-block">
      <button class='number' v-on:click='input(num)' v-for="(num, index) in numbers" :key="index">{{num}}</button>
      <button class='dot number' v-on:click='input(dot)'>.</button>
      <button class='calc number' v-on:click='calc'>=</button>
    </div>
    <div class="operations-block">
      <button class='operation number' v-on:click='input(op)' v-for="(op, index) in operations" :key="index">{{op}}</button>
    </div>
  </div>
  </div> 
</template>

<script>
export default {
  data() {
    return {
      result: '',
      numbers: ['1','2','3','4','5','6','7','8','9','0'],
      operations: ['+', '-', '*', '/'],
      dot: '.'
    }
  },
  methods: {
    input: function(char) {
      this.result += char;
    },
    reset: function() {
      this.result = '';
    },
    calc: function() {
      this.result = eval(this.result);
    }
  }
}
</script>

<style>
  .calculator{
    width: 400px;
    margin: 0 auto;
    box-shadow: 0 0 30px 3px #35495e;
  }

  .main-block{
    width: 300px;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-flow: row wrap;
  }

  .input{
    direction: rtl;
    border: 3px solid #41b88379;
    border-radius: 3px; 
    background: #ffffff !important; 
    outline: none;
    height: 60px;
    width: 391px;
    color: #35495e; 
    font-size: 44px; 
    font-family: Tahoma; 
  }

  .clear-button{
    cursor: pointer;
    background-color: #35495e;
    box-sizing: border-box;
    border: 1px solid white;
    color: #ffffff;
    font-size: 28px;
    width: 100%;
    letter-spacing: 8px;
  }

  .clear-button:hover{
    background-color: #921f2f;
  }

  .input:focus{
    border: 3px solid #41b883;
  }

  .interface{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    flex-flow: row wrap;
    width: 100%;
  }

  .number{
    width: 100px;
    height: 80px;
    background-color: #35495e;
    box-sizing: border-box;
    border: 1px solid white;
    color: #ffffff;
    font-size: 32px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    font-family: sans-serif;
  }

  .number:hover{
    background-color: #587899;
  }

  .operation{
    background-color: #41b883;
  }

  .operation:hover{
    background-color: #80e2b6;
  }
</style>